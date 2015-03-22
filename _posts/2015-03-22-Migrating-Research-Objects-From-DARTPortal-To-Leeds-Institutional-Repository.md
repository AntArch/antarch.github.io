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

The DART project established a data portal called [DARTPortal](http://dartportal.leeds.ac.uk) to hold research outputs. This was based on the [CKAN data portal](http://ckan.org/) provided by the Open Knowledge Foundation. The dedicated server has a postgresql instance and a [webdav instance](https://dartportal.leeds.ac.uk/webdav/). Bespoke ingest features were written by Dr Dave Harrison. The ingest element tools used file naming patterns to populate basic metadata for a collection with new metadata elements. Different elements in the resource name either contained the source data to enter into the metadata record for that object (i.e. date or location) or referred to a text file that contained multiple metadata elements relating to, for example, the types of processing applied to the resource. The metadata descriped this in the field title.pattern as follows:

> Where appropriate each resource has been named with the following pattern: DART_<3 character sensor/collection name>_<spatial location>_<StartDateTime YYYYMMDD with optional HHMM>_<endDateTime YYYYMMDD with optional HHMM>_<stage PRO or RAW to refer to processed or raw data>_<other stuff>.<suffix>. Hence, the file DART_T3P_DDCF_20110823_20130106_PRO.csv refers to DART data collected using the T3P Imko soil moisture probes at Diddington Clay Field between 23rd August 2011 and 6th January 2013 which has been processed and is available in a comma separated text format.

The [DART metadata schema and associated keyword lookups is documented online]. This documentation includes mappings from the DART metadata to other metadata schemas including:

* UK_AGMAP
* Dublin Core (text and RDF)
* The Archaeology Data Service (who chose to undertake a manual extract)
* Journal of Open Archaeological Data (for (semi) automated production of JOAD material)
* GEMINI
* E-Government
* Federal Geographic Data Committee

The metadata schema used by DART is rich. However, the DART data portal is a temporary entity. It was hoped that the repository landscape would become more developed and that the data hosted at DARTPortal could be re-deposited in perpetuity elsewhere - ideally with a Digital Object Identifier ([DOI](http://www.doi.org/).

For the past 18 months [Anthony Beck](http://orcid.org/0000-0002-2991-811X) has been working with [Graham Blyth](https://library.leeds.ac.uk/people/Graham-Blyth) and [Dave Harrison](http://www.engineering.leeds.ac.uk/people/computing/staff/d.g.harrison) to ingest the research objects in DARTPortal into the new Leeds Institutional Repository. There are loads of benefits including preservation in perpetuity^[which does not mean forever], better uptime and signficantly a DOI for each resource (at the lowest level of granularity).
