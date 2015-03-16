---
Date: 2015-02-02 10:47
Title: LLUCAS Sprint 01 2nd Feb - 13th Feb 2015
Category: Sprint, Agile, LLUCAS
Tags:  Sprint, Agile, LLUCAS
---

These are the sprint archives/summaries of [Anthony Beck](http://orcid.org/0000-0002-2991-811X). Anthony is a part time (60% Full Time Equivalence (FTE)) researcher on the [Leverhulme Trust](http://www.leverhulme.ac.uk/) funded project [Sustaining Urban Habitats - an interdisciplinary approach](http://www.nottingham.ac.uk/research/groups/environmental-physics-and-design/leverhulme-project.aspx) led by [Prof Darren Robinson](http://www.nottingham.ac.uk/engineering/departments/abe/people/darren.robinson).

These documents represent an archive of the work undertaken by Ant. 

Unless stated otherwise these documents are released under a [CC0](https://creativecommons.org/choose/zero/) [(+BY)](http://www.dancohen.org/2013/11/26/cc0-by/). This means that it is essentially in the public domain and you can re-use it in an unfettered way. I would, however, appreciate, but not mandate, a reference.

# Sprint 01 2nd Feb - 13th Feb 2015

A general orientation sprint. With the following sub-tasks:

* Workshops
	* Wednesday 11th Feb
	* Notes available in mindmap in /home/arb/ownCloud/Nottingham/LLUCAS/Workshops
* Create content for and deliver project web-page (need a landing page for phds)
	* Required approval from the CMS moderators to attend the course:
		* Engineering	
			* Jemma Higney	
			* +44 115 84 67556
			* jemma.higney@nottingham.ac.uk
		* Geography	
			* Claire Chambers	
			* +44 115 84 67905
			* claire.chambers@nottingham.ac.uk
* Data needs/awareness
	* Learn about Insmart from Gavin Long - help to climb learning curve
	* Request for access to AddressBase for the Nottingham area submitted to OS, approved and data in the post!
* Develop short-term plan for me
	* Described in /home/arb/ownCloud/Nottingham/LLUCAS/Sprints/Sprint01/ARB_ProofOfConceptProject.md
* Create two project summaries for MSc project using AddressBase (one to emulate InSMART).
	* Described in /home/arb/ownCloud/Nottingham/LLUCAS/Sprints/Sprint01/ABP_MSc_projects.md

## Tasks rolled over for the next sprint

* Infrastructure - software environment, processing and repository
	* Other longer term data repository issues Darren is involved in
* contact David Holland and Isabel Sargent @ OSGB. 
	* Mention my name and ask if they can discuss what has been happening with their 3D city models research. I know Bournemouth was well covered in research (10 years ago ish) but it would be great to find out if/where this has been rolled out to. Also if they have plans could we ask they consider Nottingham etc. I have not kept  up with what has been happening in Photogrammetric Services at OS (and what LiDAR they have been looking at) and so would be good to know.

# Retrospective

A general review of thoughts/issues etc that summarise outcomes from the sprint and to take forward to the next sprint.

## What went well?

* Building up relationships with people
	* Gavin Long
	* Lauren Halsted
	* John Milner (Systems Development Officer - Geography)
* Accessing Address base data from OS
* Potential MSc student (Jordan Clydesdale) to look at AddressBase elements in InSMART

## What have we learnt?

* We can add some value to the housing metric produced by Gavin Long in terms of processing of O/S MasterMap data and integration of AddressBase Premium
* If the RSS rendering of external content is reasonable then internal CMS system may be OK
* The repository landscape has, inevitably, improved in the last few years: The EU FP7 project [Zenodo](http://zenodo.org/faq) is a good example

## What could we do better?

* There seems to be some uncertainty in terms of collaborative environments and sharepoint use with the university - this is likely to get worse for users outside the Nottingham domains.

## What still puzzles us?

* What is going on in the university in terms of data repositories, open science, collaborative working (sharepoint?)
	* Additionally how any developments can be used externally
* Workflows. Jeremy said to get in touch with Didier Libervichy. He is a spatial statistician working on quality and uncertainty issues in workflows. 
* Databases - Oracle/Postres/Nosql - where to go. What to use
* How does the CMS system deal with harvesting content from external or internal systems (bibliographies, papers, sharepoint, slideshare) and promoting content on other frameworks (twitter, facebook (please have some automated system so I don;t have to do anything in facebook))

## What is blocking activity

* CMS training - I am booked for April and have flagged a position for any Feb/March dropouts. This is unlikely to match to Darrens timeframe.
	* Jemma has kindly agreed to host content until training has been approved.
* I need to discuss with Darren what the external hosting requirements are. Are we going to put content in slideshare, scribd, youtube, mendeley/zotero? If we are, then we should get a shortlist of the ones we will use so that the *Web Team* can see how they can render any data in an RSS feed.
* An external landing page url. http://llucas.info/
* For the MSc student we would need Darrens approval.

# Task summary

## Create content for and deliver project web-page (need a landing page for phds)

Content has been created for the website in /home/arb/ownCloud/Nottingham/LLUCAS/Sprints/Sprint01/20150204_LLUCAS_Website_Content.md with supporting images in /home/arb/ownCloud/Nottingham/LLUCAS/Sprints/Sprint01/Outputs. These have been passed over to Darren for review. This should make it significantly easier for me to hand this content over to someone to put onto the website (if I am not allowed to self host). 

I have been booked on the April course but have flagged to see if a position will become available 

### General CMS fitness for purpose

I have spoken to John Mitchell and Jemma to try to determine what the CMS does and need to determine if it is fit for what the project wants to do. 

Like any CMS it should provide an easy way to host text and content supported by a backend database. The issues come when we consider the following:

* University branding
* URL of any landing page
* Social media integration
* If the system can be extended (plugins)
* Licensing
* Automated harvesting of other content on the web

The last two points are probably the most important. 

Keeping everything in the university CMS has some advantages - particularly in terms of longevity and archiving after the project concludes. However, if we need to hand-crank pages and content because we can't harvest information stored elsewhere on the web (such as project twitter feeds, documents on scribd, presentations on slideshare, etc. ) then it becomes a burden.

Availability of funcationality provides us with 3 options:

* Use the university CMS
* Host our own CMS infrastructure internally (this might be unlikely - although there are internal websites that use their own CMS)
* Host our own CMS infrastructure externally

I had a meeting with Jemma on 20150209 to discuss these issues.

#### Branding

As this is a project there are no major branding restrictions

#### Landing page

This is flexible: We can buy our own unique url and point to this from an internal host.

I would recommend this - this means we can use something internally and point to the external link. If the CMS does not do what we want we have the flexibility to change this external page in any way we saee fit. http://llucas.info/ is free.

#### Archiving

If we host externally at project completion we can *scrape* the external site and host back within Nottingham (or deposit in the British Library).

#### Social media

The current CMS supports LinkedIn and Twitter connections. There is no internal demand for facebook (which I think is a good thing).

#### Automated harvesting of content

Jemma said this is not supported by the CMS. Although the CMS does have some plugins and can be extended. I followed this up with the web-team (Jemma said to speak to David Aldred, but I ended up speaking to one of his colleagues who was very helpful). They said they have an RSS feed reader that can be used to render content from external systems - this may be perfect. However, we do need to see examples of how this content would be rendered. 

Requirements - make a list of external hosting services for content.
 

#### Licensing

There doesn't seem to be any strategy on licensing.

As we are starting to generate content, including illustrations, we should also consider what we are going to do with this content. I would strongly advocate that any original content is hosted on Wikimedia commons under either a [CC-BY](https://creativecommons.org/licenses/by/3.0/) or a [CC0](https://creativecommons.org/choose/zero/) [(+BY)](http://www.dancohen.org/2013/11/26/cc0-by/) licence. Where there is a clear author then let them place it on there on user account. Where it is unclear host it on a project account. I would also recommend embedding the licence and attribution into the image or graphic - this means that re-users are encouraged to leave it in (and thereby reference the source - completing their side of the licence bargain). This is how I have started to host [my more recent content on wikimedia commons](https://commons.wikimedia.org/wiki/File:SQL_Joins.svg) (see Figure \ref{SQLJOIN}).

![my more recent content on wikimedia commons\label{SQLJOIN}](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9d/SQL_Joins.svg/1000px-SQL_Joins.svg.png)

## Infrastructure

Caveat - we could take everything outside of university infrastructure. I have made the assumption we want to do everything in collaboration with the university. If there are too many compromises then we can review this.

Data and server environments - this would be best co-ordinated with the **virtualisation farm**. This is managed by *Chris Parry* (who is head of partnering and has responsibility for the university data repository: chris.parry@nottingham.ac.uk - +44 115 84 13196). A meeting will be convened with Chris. 

Internal Workflow environments. Jeremy said to get in touch with Didier Libervichy. He is a spatial statistician working on quality and uncertainty issues in workflows. 

### Email to Chris Parry

Title: University Data Repositories

Dear Chris,

John Milner passed me your details.

My name is Anthony Beck I am a recently appointed part-time Research Fellow on the [Leverhulme Trust](http://www.leverhulme.ac.uk/) funded project [Sustaining Urban Habitats - an interdisciplinary approach](http://www.nottingham.ac.uk/research/groups/environmental-physics-and-design/leverhulme-project.aspx) led by [Prof Darren Robinson](http://www.nottingham.ac.uk/engineering/departments/abe/people/darren.robinson). I started last week.

As part of this project we are planning on building a data repository and data processing environment (distinguishing between our archiving and metadata commitments and our data processing requirements). On my [last project I built a CKAN based data repository](http://dartportal.leeds.ac.uk) with a rich metadata environment - I am in negotiation with Leeds library about migrating this over to their new institutional repository and minting DOIs for the different research objects. I digress.

I appreciate that this is a rapidly changing area - especially as RCUK and the funding councils develop guidance. To avoid re-inventing the wheel I would like to find out:

* what data repository and analysis initiatives are ongoing in the university
* get guidance in terms of university approved licensing and metadata options
* what accreditation systems may be in place (I'm trying to avoid this as much as possible by taking an Open Science route).

I am also interested in what collaborative tools are available in and supported by the university (from desktop (using sharepoint, google docs, markdown, etc.) to analysis (taverna, alteryx)) and the server platforms for hosting such services (virtual, static etc.).

The project does have resources to contribute to some/all of these activities.

Would it be possible for you to point me in the direction of any supporting information for these activities. Alternatively we could meet up (I appreciate you are likely to have a busy schedule). I work 3 days a week (Monday to Wednesday).

I will follow this message up with a call.

Best wishes

Ant



## Data needs/awareness

The OS have kindly given us access to AddressBase Premium and AddressBase Plus

### Chat with Gavin - summarise

### Accessing AddressBase Premium

AddressBase Premium will add some significant value to the housing work. AddressBase Premium (ABP) as a product is managed by Geoplace a consortium of Ordnance Survey and Local Government. Unfortunately, there is no direct mechanism in place to access ABP directly for academic research. Some of the issues and solutions are described in [Karl Hennerman's blog](https://karlhennermann.wordpress.com/2014/05/14/getting-uk-address-data-for-academic-research/). The upshot is we need to send a brief e-mail to Ordnance Survey (universityenquiries@ordnancesurvey.co.uk) requesting access to the data.

#### Email to OS

To whom it may concern,

Request for academic use of AddressBase Premium and AddressBase Plus data from within the [city of Nottingham boundary](https://secure.nottinghamcity.gov.uk/mRegisterOfficeBooking/NottinghamCityCouncilAdministrativeBoundary.pdf) for use within the InSMART and Sustaining Urban Habitats projects at Nottingham University.

Principal Investigator: [Prof Darren Robinson](http://www.nottingham.ac.uk/engineering/departments/abe/people/darren.robinson)

Theme Leaders: [Dr Doreen Boyd](http://www.nottingham.ac.uk/geography/people/doreen.boyd) and [Jeremy Morley](http://www.nottingham.ac.uk/geography/people/jeremy.morley)

Data Contact: Dr Anthony Beck (anthony.beck@nottingham.ac.uk)

The [InSMART project](http://www.insmartenergy.com/) brings together cities, scientific and industrial organizations in order to implement a comprehensive model for enhancing sustainable planning addressing the current and future city energy needs through an integrative and multidisciplinary planning approach. This approach will identify the optimum mix of short, medium and long term measures for a sustainable energy future, addressing the efficiency of energy flows across various city sectors with regards to economic, environmental and social criteria and paving the way towards actual implementation of priority actions.

Extensive technical expertise and specialised tools and models will be used to create a platform for implementation of the project idea. The approach will be used by four city partners in Greece, Italy, the UK and Portugal, all actively involved in developing a more sustainable energy system. Each city’s energy system will be analysed, covering all relevant sectors and a comprehensive GIS energy database will be developed. Apart from being a valuable planning tool the GIS database will inform and be linked to the TIMES energy systems model. This will be used to analyse the cost-optimal mix of measures required to meet sustainable energy targets taking into account exogenous parameters (e.g. environmental targets, city expansion). These measures will be further assessed with respect to non-technical criteria using a multi-criteria decision making method (PROMITHEE) that will address economic, environmental as well as social issues.

The Nottingham component of this research project utilises National Land and Property Gazetteer (NLPG) data provided by the Nottingham City Council. The NLPG data is now exposed through the AddressBase family of data provided by Geoplace. By using AddressBase Premium and AddressBase Plus products the InSMART project will be able to build a more scalable research platform that can be seamlessly applied to different UK cities and respond to data changes more effectively (by applying epoch based Change only Updates).

These benefits will also apply to the Sustaining Urban Habitats project (website is currently under construction). Sustaining Urban Habitats: An Interdisciplinary Approach is funded by a prestigious Leverhulme Programme Grant. The ambitious aim of this project is to transform our understanding of how sustainable cities, and by extension our species, can be. This project commenced in early 2015 and will complete in 2019. 

AddressBase data will prove to be a crucial resource for the *Measurement and Data* themes in this project.

I look forward to hearing from you. If you require further information on either project please do not hesitate to ask. 

Yours sincerely


Anthony Beck

Research Fellow: University of Nottingham.

#### Bob Barr and [core reference geographies](http://www.slideshare.net/geocommunitylive/bob-barr-what-are-core-reference-geographies)

Karl's website had a reference to Bob Barr and ABPREM which I followed up. I know Bob had a pop at the UK addressing infrastructure and sees addresses as a *Core Reference Geography*. These are geographic datasets which:

* Are definitive
* Should be collected and maintained once and used many times
* Are Natural monopolies
* Have variable value in different applications
* Have highly elastic demand

He argues that the following are candidate core reference geographies:

* Geodetic Framework
* Topographic Mapping (including height)
* Geographic Names
* Addresses
* Streets
* Land and Property Ownership
* Hydrology / Hydrography
* Statistical Boundaries
* Administrative Boundaries

Much of this data is already available and collected by Public Bodies (some of whom may be independent trading arms - such as the Ordnance Survey). Some of these data may already being opened up as part of the UK governments Open Data agenda. Some of this data is very relevant to the projects. This is tied in with the view of Business Innovation and Skills and their white paper on [*An open National Address Gazetteer*](https://www.gov.uk/government/uploads/system/uploads/attachment_data/file/274979/bis-14-513-open-national-address-gazetteer.pdf).

## Modelling

We need data that will support the following modelling exercises (which in turn go through the simulations environments)

* Model
	* Building
	* Energy demands
	* Multi modal transport
		* 4 stage modelling
		* 6 stage modelling
	* District heating networks
	* Demands from LV networks
	* Demands from storage
	* Model land-user transport interactions

## Notes about the different general data categories

* Data differences
	* Calibration data
	* Evaluation data
	* Sensor data
		* In terms of sensoring results
	* Data agencies
		* Traffic count
		* Ofgem


## Other activities TBC

* Speak to the photogrammetry dept in Stuttgart
	* Developing an ADE extension to CityGML for Stuttgart
* Doreen - Speak to Geomatics group
	* Kyle

## Develop short-term plan for me

Flesh out in week 2

## Other longer term data repository issues Darren is involved in

* Strategic research and innovation agenda
	* Darren is writing this
	* Would like
		* 2 or 3 city observatories
		* Very highly instrumented
		* Put in a strong bid for Nottingham
	* Funding
		* Europe
		* ESRC


* Annex 66
	* Behavioural modelling
	* Put together a data repository
		* Can make the data available to the academic community
	* Conversation around this - later in the week
	* I want to think about this in terms of the carrot and stick approach to encouraging participation - the strategy and firewalling option has implications for the licenses. There may be a short-term/long-term incompatibilities.
