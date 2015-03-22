---
Date: 2014-03-05 20:00
Title: DART licences and the ADS
Category: DART, archaeology, licences, ADS
Tags: DART, archaeology, licences, ADS
layout: post
---

This is a place where I am forming thoughts/discussions about licensing and the ADS in relation to the DART archive. 

Data from the [DART Portal](http://dartportal.leeds.ac.uk/) is slowly appearing on the [Archaeology Data Service](http://archaeologydataservice.ac.uk/archives/view/dart_ahrc_2013/overview.cfm). The slowness is mainly of my making. 

However, one thing which has cropped up is the licensing of the data. At DART we have followed the [guidelines of The Open Data Institute](http://theodi.org/guides/publishers-guide-open-data-licensing) and separated out creative content from data content. Hence, the DART content is either [CC-BY](http://creativecommons.org/licenses/by/4.0/)* or [ODC-BY](http://opendatacommons.org/licenses/by/) respectively. To be honest I'd quite like to drop the -By (by attribution) clause, but this may push the DART partners too far. There is a [post on ccZero+ by Dan Cohen that advocates this](http://www.dancohen.org/2013/11/26/cc0-by/). I erroneously stated to the ADS that DART was using the ODBl licence (which is by attribution and share-a-like) - we are not.

The ADS don't allow this. Their [terms of use](http://archaeologydataservice.ac.uk/advice/termsOfUseAndAccess) state:
> Unless a form of Creative Commons licence is clearly attached to a particular collection and the Creative Commons logo is prominently displayed on that collection's introduction page the following terms of use and access apply.

This means that prior to CC4 data licences aren't recognised by the ADS (the irony is not lost on me). The argument is that none of the other datasets held by the ADS have used the Open Data Commons licences so they don't want to start using it now. This is short sighted as the Open Data Commons licences will gain traction (it is advocated by the ODI) and they may be putting off a problem they will need to tackle in the future. 

However, this does raise a number of broader, and I would argue more significant, issues:

1. We should use appropriate licences for the appropriate content. ODC-By is the right licence for this data. Just because other individuals do not use this licence does not invalidate this position. This argument was stronger before CC4.
2. The ADS licence is bespoke and does not map to national or international licence schemes (unlike Open Data Commons). 
	3. This could lead to longer term licence incompatibilities (especially if licence calculas [(or machine-readable rights statements)](http://schema.theodi.org/odrs/) are introduced). This is important for automating legal compliance when machine aggregation of heterogeneous resources occurs.
	4. DART could release their data under ODBl (by attribution and share-a-like). This would create an immediate incompatibility with the non-standard ADS licencing scheme. This would mean that we **could not** release our data through the ADS under the ADS's current licencing mandate.
3. The ADS licence is also more restrictive than the DART licences.
	4. In particular the ADS licence contains a Non-Commercial clause. As part of its scope to maximise engagement, impact and re-use DART encourages commercial exploitation of its outputs.
	5. Given the position of the government, RCUK and other funding councils on data access, it may be that government mandates all publically funded research is made available under more permissive licences than the ADS currently use.

These issues do need to be considered.

In the case of DART this should not be a problem. Our licences are permissive (by attribution is the only clause we have included). This means the ADS can do anything they want with our resources *as long as they cite the source*. In our case this would be the individual resource objects or collections on the DART portal. This is a good thing as the metadata on the DART portal is much richer than the metadata held by the ADS. 

The down-side is that we do not have the resources to keep the DART portal in place in perpetuity. The up-side is we are in discussion with Leeds University to migrate all the data objects over to the new institutional repository with sparkling new DOIs (it should be noted that ADS will only accept a sub-set of the full DART archive) and we can transfer the metadata held in CKAN over the Open Knowledge Foundation [dataHub](http://datahub.io/). In theory nothing should be lost. Practice, inevitably, may be something different.

I have not argued here that I believe that aerial photographs used for interpretative purposes are, like every other form of remote sensing, data and not creative content. I will save this for another day.

*Cameron Neylon has just let me know that CC-BY version 4 does cover data - that is good. [CC4 was published in November 2013](http://wiki.creativecommons.org/4.0). That said, we are still following the ODI guide.

*If you have anything to add to this please let me know and I will update the post accordingly*

