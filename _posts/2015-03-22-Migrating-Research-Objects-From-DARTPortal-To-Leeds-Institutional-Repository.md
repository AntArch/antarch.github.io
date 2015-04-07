---
date: 2015-03-22
title:  'Migrating Research Objects From DARTPortal To Leeds Institutional Repository'
author: Anthony Beck, Dave Harrison, Graham Blyth
layout: page
category: DART, data, repository, Leeds, Open Data, CKAN, e-prints
tags: DART, data, repository, Leeds, Open Data, CKAN, e-prints
bibliography: references.bib
csl: harvard.csl
abstract: |
  Please add in your name to the author list.

  Written using [CommonMark](http://commonmark.org/) formatting: an unambiguous implementation of Markdown for scholarly writing.
  
  Can be rendered to other formats as using [Pandoc](http://johnmacfarlane.net/pandoc/). To render to PDF with a table of contents use the following:

  pandoc -f markdown -t latex -N -V geometry:margin=1in  <location and name of file> --filter pandoc-citeproc --latex-engine=xelatex --toc -o <location and name of file>.pdf


  \newpage
---

Details about how the research objects held on [DARTPortal](http://dartportal.leeds.ac.uk) we're migrating to the Leeds Institutional repository.

\newpage

# Background

The DART project established a data portal called [DARTPortal](http://dartportal.leeds.ac.uk) to hold research outputs. This was based on the [CKAN data portal](http://ckan.org/) provided by the Open Knowledge Foundation. The dedicated server has a postgresql instance and a [webdav instance](https://dartportal.leeds.ac.uk/webdav/). Bespoke ingest features were written by Dr Dave Harrison. The ingest element tools used file naming patterns to populate basic metadata for a collection with new metadata elements. Different elements in the resource name either contained the source data to enter into the metadata record for that object (i.e. date or location) or referred to a text file that contained multiple metadata elements relating to, for example, the types of processing applied to the resource. The metadata descriped this in the field *title.pattern* as follows:

> Where appropriate each resource has been named with the following pattern: DART_<3 character sensor/collection name>_<spatial location>_<StartDateTime YYYYMMDD with optional HHMM>_<endDateTime YYYYMMDD with optional HHMM>_<stage PRO or RAW to refer to processed or raw data>_<other stuff>.<suffix>. Hence, the file DART\_T3P_DDCF\_20110823\_20130106\_PRO.csv refers to DART data collected using the T3P Imko soil moisture probes at Diddington Clay Field between 23rd August 2011 and 6th January 2013 which has been processed and is available in a comma separated text format.

The [DART metadata schema and associated keyword lookups is documented online](https://docs.google.com/spreadsheets/d/1Zyx49aPpl8d1ud6TmQ6T-ohXq9LdlHPICkotE8MYh5E)^[Graham - note this contains the data dictionaries ]. This documentation includes mappings from the DART metadata to other metadata schemas including:

* UK_AGMAP
* Dublin Core (text and RDF)
* The Archaeology Data Service (who chose to undertake a manual extract)
* Journal of Open Archaeological Data (for (semi) automated production of JOAD material)
* GEMINI
* E-Government
* Federal Geographic Data Committee

The metadata schema used by DART is rich. However, the DART data portal is a temporary entity. It was hoped that the repository landscape would become more developed and that the data hosted at DARTPortal could be re-deposited in perpetuity elsewhere - ideally with a Digital Object Identifier ([DOI](http://www.doi.org/)).

For the past 18 months [Anthony Beck](http://orcid.org/0000-0002-2991-811X) has been working with [Graham Blyth](https://library.leeds.ac.uk/people/Graham-Blyth) and [Dave Harrison](http://www.engineering.leeds.ac.uk/people/computing/staff/d.g.harrison) to ingest the research objects in DARTPortal into the new Leeds Institutional Repository. There are loads of benefits including preservation in perpetuity^[which does not mean forever], better uptime and signficantly a DOI for each resource (at the lowest level of granularity).

Graham Blyth has been leading the development of the institutional repository for Leeds University. They have developed a metadata schema (which although not as rich as the DART schema has much in common). They also share a common structuring approach to DART where *research objects* are grouped into *collections*. 

# Bulk Ingest system for the Leeds Repository

A system has been developed for bulk ingest. This can be used to migrate the DART data into their e-prints based repository environment.

Essentially it requires the following:

1. Each *collection* has its own folder
2. All the *research objects* are stored in this folder
3. A single text file holds metadata for the collection and research objects

The metadata file is a flat structure that looks something like this:

eprintid|rowid|documents.docid|documents.rowid|title|identifier|doi|funders
----|----|----|----|----|----|----|----
1|1_0|||DART weather data|||SaHP
1|1_1||||||AHRC
1|1_2||||||EPSRC
1|1_3|1|1_0||||
1|1_4|2|2_0||||
1|1_5|3|3_0||||
1|1_6|4|4_0||||

Unfortunately - I haven't been able to get Jekyll to render markdown tables properly.

As can be seen the structure is a bit of a hack that allows 1 to many relational data to be expressed in a single flat file. The file is structured in the following ways:

* Field *EPrintID* represents the identifier of the collection
	* Where this is the same everything is in the same collection
* Field *RowID* helps represent the 1-many relationships for the collection
* where there is **ONLY** an *EPrintID* and *RowID* then this contains metadata about the collection: 
	* 1_0 is the default row and contains most of the metadata about the collection 
	* 1_x is where there is a 1-many relationship in terms of required attributes for the collection metadata only
		* Note that multiple 1- many attrributes for different fields can be held on the same 1_x row. Although I would expect that no problems would be caused if there was only 1 attribute held in each 1_x row (which would be easier to represent in a relational model))
* *documents.docid* and *documents.rowid* refer to research objects within the collection. 
	* If there are 1-many relationships about the data then we maintain the same documents.docid and increment the documents.rowid 

# Point 1 and 2 - Collection and folder physical preparation

This is done. Not a problem.

# Point 3 - Metadata creation for ingest

The backend CKAN system is not ammenable to direct SQL extract - and the OAI-PMH in the system doesn't do what we want it to do. Dave will create a python script that creates this metadata by parsing the collections and resources. Because we have a naming pattern this is fine (it basically repurposes the ingest system we used for CKAN and matches to the Leeds Schema)

## Mapping between the DART schema and the Leeds Institutional Repository schema

This has been started and is [documented online](https://docs.google.com/spreadsheets/d/1Zyx49aPpl8d1ud6TmQ6T-ohXq9LdlHPICkotE8MYh5E). However, it does require revision. I have just understood the difference in the colour coding of the schema details given to me by Graham:

* Red - compound primary key
* Green - Collection metadata
* Blue - Resource metadata

(Forgive colour issues - I'm colour blind). This sheds a different light on things. For example different resources in our collection are collected at different dates. Hence our dates reflect differences at the resource level and not at the document level. 

-------

The initial mapping was against the backend model (see column 'DART mapping (formal)'. However, as we couldn;t extract what we anted from this backend we have decided to go back to our ingest scripts. The DART ingest scripts worked as follows:

* A folder contained data files and metadata files
	* All data files had a naming convention (described below). Each data file is prefixed with the value DART_
		* The elements in this convention supply some values for the object level metadata either directly or via lookup
	* At least one file called *metadata.txt* that holds the collection level metadata
	* Between 0 and many other metadata *txt* files with a name which matches an element in the naming convention

The DART naming convention was:

> Where appropriate each resource has been named with the following pattern: DART\_\<3 character sensor/collection name\>\_\<spatial location\>\_\<StartDateTime YYYYMMDD with optional HHMM\>\_\<endDateTime YYYYMMDD with optional HHMM\>\_\<stage PRO or RAW to refer to processed or raw data\>\_\<other stuff\>.\<suffix\>. Hence, the file DART\_T3P\_DDCF\_20110823\_20130106\_PRO.csv refers to DART data collected using the T3P Imko soil moisture probes at Diddington Clay Field between 23rd August 2011 and 6th January 2013 which has been processed and is available in a comma separated text format.

The ingest system works as follows:

* iterates over the data files in the folder. For each data file
	* Creates a metadata record based on the values in the file *metadata.txt*
	* Splits the object filename based on '_'. It iterates over these elements and adds or overwrites values in the metadata record based on:
		* Date values (start date or end date of collection)
		* Matching metadata *txt* file
			* For example if the name contains the value RAW then the code looks for a matching textfile called *RAW.txt*. If it finds this file then the values from this file are used to extend or overwrite the metadata values.

This conceptually is closed to the approach taken at Leeds. We can use the values in the *metadata.txt* file to populate metadata values at the **collection** level. We can then use the values embedded in the field name or the values in the associated metadata *txt* files to populate metadata values at the **object** level.

I have added in a new column 'DART ingestfile mapping' in the [DART metadata mapping](https://docs.google.com/spreadsheets/d/1Zyx49aPpl8d1ud6TmQ6T-ohXq9LdlHPICkotE8MYh5E/edit#gid=740656025) file to reflect this. 

**One concern is the string length restrictions on schema values at Leeds (I have had no response to my query concerning which fields have > 250 characters). I suggest we do what we need to and then this is truncated by the Leeds team.**

## Thoughts on the Leeds repository structure

The character restriction on fields may be too conservative. It wodl be helpful if the data model was published.

The object level metadata for the Leeds schema is sparse: greater emphasis is given to the collection. In the short-medium term that may reflect the nature of the data (i.e. everyone zips up their stuff and dumps it in the e-prints repository). In the longer term that may be a problem - especially if their are DART like projects. 

### Enriching the date elements at the object level

For the physical sciences in particular data may well be segmented into collection periods. Hence for longitudinal projects there may be many datasets within a collection which reflect the same sensor (or mode of collection for a survey) which are collected on different dates or over different durations. I would suggest date level metadata is added at the *Object level*.

### Enriching the 'creator' elements at the object level

I would expect RCUK to add career enhancement incentives for data deposition. This means that 'well cited' data sets (hopefully representing *gold standard* data) may be pivotal for career progression. There is no granularity at the object level in this schema to identified who created the object resource. One simply can not assume it is the same as the *collection*. I would consider adding more fields here.


# What to do about the richer metadata held in DART

Part of the python script will create a metadata file for each resource object with the following pattern (which might change) <resource name without suffix>&'_metadata.txt'. We will create this for each resource. 

