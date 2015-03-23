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

Graham Blyth has been leading the development of the institutional repository for Leeds University. The have developed a metadata schema (which although not as rich as the DART schema has much in common). They also share a common structuring approach to DART where *research objects* are grouped into *collections*. 

# Bulk Ingest system for the Leeds Repository

A system has been developed for bulk ingest. This can be used to migrate the DART data into their e-prints based repository environment.

Essentially it requires the following:

1. Each *collection* has its own folder
2. All the *research objects* are stored in this folder
3. A single text file holds metadata for the collection and research objects

The metadata file is a flat structure that looks something like this:

|eprintid|rowid|documentsdocid|documentsrowid|title|identifier|doi|funders|
|----|----|----|----|----|----|----|----|
|1|1_0|||DART weather data|||SaHP|
|1|1_1||||||AHRC|
|1|1_2||||||EPSRC|

eprintid|rowid|documents.docid|documents.rowid|title|identifier|doi|funders
----|----|----|----|----|----|----|----
1|1_3|1|1_0||||
1|1_4|2|2_0||||
1|1_5|3|3_0||||
1|1_6|4|4_0||||

As can be seen the structure is a bit of a hack that allows 1 to many relational data to be expressed in a single flat file. The file is structured in the following ways:

* Field *EPrintID* represents the identifier of the collection
	* Where this is the same everything is in the same collection
* Field *RowID* helps represent the 1-many relationships for the collection
* where there is **ONLY** an *EPrintID* and *RowID* then this contains metadata about the collection: 
	* 1_0 is the default row and contains most of the metadata about the collection 
	* 1_x is where there is a 1-many relationship in terms of required attributes for the collection metadata only
		* Note that multiple 1- many attrbites for different fields can be held on the same 1_x row. Although I would expect that no problems would be caused if there was only 1 attribute held in each 1_x row (which would be easier to resreate in a relational model))
* *documents.docid* and *documents.rowid* refer to research objects within the collection. 
	* If there are 1-many relationships about the data then we maintain the same documents.docid and increment the documents.rowid 

# Mapping between the DART schema and the Leeds Institutional Repository schema

I have started this - will finish off tonight. Mainly a 1-1 mapping. Nothing hugely unexpected.

# What to do about the richer metadata held in DART

Quite simply we should turn this into a text file and make it available through the repository. Each of these metadata records should have a row in the Leeds Institutional metadata file described above. It should be a csv file with header. The question is the degree of granularity (a record per research object or a record per collection). 

# Dave/Graham- what I hope we should achieve.

Getting the actual data prepared is a doodle - we've already done it. By giving him an account Graham can get access to the data folders via WebDAV. What is missing is the metadata summary for Leeds and a record of the DART metadata for each object/collection as a text file.

## Metadata summary for Leeds

I'd like to believe we can query this out directly from the back-end tables. Dave - can we have a crack at doing this tomorrow?

## Metadata summary for each object/collection

Do either of you have opinions on the degree of granularity? Or should we have our cake and eat it i.e. a single record for each object with a single metadata entry and a multi record object for the collection. This is in part going to be constrined by the ease of metadata creation. 

Thoughts/preferences from either of you?


