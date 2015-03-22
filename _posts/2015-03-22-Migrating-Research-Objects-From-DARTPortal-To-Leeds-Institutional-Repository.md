---
date: 2015-03-22
title:  'Migrating Research Objects From DARTPortal To Leeds Institutional Repository'
author: Anthony Beck, Dave Harrison, Graham Blyth
layout: post
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

Details about how the research objects held on [DARTPortal](http://dartportal.leeds.ac.uk) were migrated to the Leeds Institutional repository.

\newpage

# Executive summary

The OSM_GB project was described as follows:

>The project is a co-operative research project between the University of Nottingham‘s Centre for Geospatial Science, and 1Spatial. We will be exploring means to apply country-wide data quality improvement rules to Open Street Map data of Great Britain with a transformation to the British National Grid projection to produce an “OSM-GB” product.

>Alongside production of an OSM-GB output we are interested in how 1Spatial’s Radius Studio product, which we will be using for the rule-based quality improvement, can be used to adapt the output for different uses and to report locations of errors to feedback to the OSM community.

>The OSM-GB outputs are not intended to replace the main Open Street Map database but are intended to provide a version with specified data quality characteristics. The OSM-GB data will not be directly edited by users – updates will be carried out in the source OSM data and will then propagate through to OSM-GB via a regular update cycle.

The project itself was completed in 2013. The service was left intact but no resources were in place to manage, maintain and migrate the service. Inevitably the service was hacked and is now unavailable. Prior to the service going down it was in use by a range of different stakeholders from industry, research and the public sector. Whilst there was some goodwill surrounding the service this will evaporate the longer the service is down. 

Jeremy Morley, Amir Pourabdollah and Anthony Beck had a brief meeting on 20150318 to discuss what could be done with the service. All three felt that the service should be resurrected. Ideally it should have the following characteristics

1. The original OSM_GB infrastructure should be pared to expose only the critical elements
	* Remove the wordpress which is an on-going security risk
1. The service should remain within an *academic* setting
	* This should also obviate any UoN Intellectual Property issues (if applicable - it would be nice to ensure that these were clearly stated up front)
1. Be free at the point of use and available to all
	* This does not entail any service level commitments
1. The 1Integrate service (Radius Studio has been re-branded as 1Integrate) will need licencing
	* Provided by 1Spatial?
1. The 1Integrate service will be re-usable as a SAAS research and teaching platform within Nottingham University
	* Managed by Anthony Beck and 1Spatial
1. The workflow framework for OSM_GB will be managed by Anthony Beck with support from Amir Pourabdollah
1. The service could be enhanced by undergraduate or masters research projects
	* There is no expectation that the service shall be developed or enhanced
1. Server management should be institutionally managed by Nottingham University

The most important issue is the final point. The underlying workflow and analytics for OSM_GB are still valid - the problem is the resources to manage the server environments. Whilst this is viewed from a project perspective it will always remain a problem. However, the underlying landscape of academic infrastructure provision is changing. The government, through the funding councils, is starting to change the way that academia publishes and shares research outputs and is encouraging universities to maximise research impact within public and industrial settings. This is most obviously seen in the *open access* initiative to improve availability to research papers. Improved access to data, under more open licences, has been recommended by RCUK and is mandated by EPSRC. The underlying corrollary is that data analytics and data services will be part of the future of university research outputs. This will require the management and maintenance of services like OSM_GB. It is hoped that in the long-term OSM_GB will become part of a suite of managed services offered by the University of Nottingham in perpetuity (or at least as long as theycan demonstrate there is a demand for the service and that the service is providing impact which is beneficial to UK funding agencies).

# Proposed Tasks

## Resurrect the service (kick off - end of April 2015 - completion May 2015)

The aim of this task is to get the services back up and running

Tasks include:

* Knowledge transfer from Amir to Ant
* Server patching and potential consolidation (i.e. moving services from the linux server to one of the windows servers)
* Paring down OSM_GB content
	* Removing the WordPress component (or migrating this to an external host via a pointer)
	* This may include scraping and then archiving the project web-pages with the British Library
* Configuring the service based upon server configuration
* Testing the service
* Publicly exposing the service

## Securing and maintaining the service platforms (post May 2015)

The aim of this task is to provide long-term hosting and associated server/DBA management. 

By removing the at-risk components (such as Wordpress)  the service will become more stable. However, it will still need managing in terms of server and database maintenance. In terms of the latter there is DBA level database maintenance and operational level maintenance. 

Ant and Amir will look after the operational maintenance. However, the server and DBA components need resourcing. This can be done in one of two ways (assuming it stays within the University of Nottingham):

1. The UoN takes ownership of the server and DBA maintenance at zero cost (as part of building a data analytics environment)
	* This has potential but may take some time to implement
1. The UoN is paid to manage this environment
* Find out how much this would cost?

## Determining credit and impact (on-going)

Impact and credit may be key in terms of getting buy-in from key stakeholders. As already discussed the government is redefining the metrics surrounding the value of University outputs. Cross sector/societal impact will be key to this. This service will provide such impact. However, in the first instance this may need demonstrating to the university. This can be demonstrated through letters of support^[any other approaches that are quick and easy?]. We could ask for letter of support from the following (with suggested themes)^[first cut - please add more]:

* University of Nottingham (Jeremy, Muki, etc.) on the theme of:
	* General societal impact
	* Teaching and Learning resources
	* Provision of stable data analytics/web services that are a bridge between research and industry
	* Ways of building on and exploiting OSM
* Industry (Mike Sanderson, Harry Wood, Mike Saunt, Steven Feldman, AGI, etc.)
	* Quality and provenance
	* Platform to build on
	* Pathways to exploiting research
	* Use of OSM in UK projection
	* Ways of building on and exploiting OSM
* Public Sector (whom?)
	* Quality and provenance
	* Platform to build on
	* Pathways to exploiting research
	* Use of OSM in UK projection
* GDI (Jeremy)
	* OS

In addition to such letters of support those who contribute to the project should be able to exploit this in their own PR. 

## Longer term developments

*A place where I’ve just put some thoughts*

### Change management

How do we institute and manage change, provide service stability (i.e. if products are built on this then changes to the way the service is exposed can break downstream dependencies^[this might be the basis for a ‘paid for’ service - whereby such stability is part of the product]).

### Removal of the Oracle dependency

Oracle is used in the current stack as it was a requirement of RadiusStudio. 1Integrate has a PostGreSQL version in development. That would simplify the workflow quite dramatically. 

### Server infrastructure - this will inevitably die :-(

The current server hardware will go out of maintenance^[when?]. Consideration could/should be given to migrating to virtualised servers.

### Steering group

Is such a thing required? If so should have a light touch and low overhead -  Discussion group?

# Task Resourcing issues

## Licensing 

The software stack requires (beyond server licences) licences for:

* Oracle
* 1Integrate (was Radius Studio)

The Oracle licence is available through the UoN. Although there is some uncertainty as to how long this may remain. The UoN is strongly Microsoft based. The Centre of Oracle Spatial excellence link may not be maintained. 

1Integrate is provided by [1Spatial](http://1spatial.com/). The current licence for OSM_GB is likely to be up for renewal. 1Spatial have agreed^[verbally - need to get commitment] to renew this licence for the OSM_GB service. It would be beneficial is this licence could be used for other things apart from OSM_GB to support research and teaching within the UoN. There may also be interest in developing a public rule authoring environment (crowd develop rules or an industry/research rule sandbox).

## Support and other technical consulting

Some DBA and server management

Service configuration (1Spatial + others 


## Financial

### Software licences

Primarily 1Spatial - speak to Mike

### Server environment

Community/UoN

### Staff/Consulting
Server management time

DBA management time

Service management and development


# Other issues

Any other issues
