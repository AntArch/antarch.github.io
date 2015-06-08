---
Date: 2015-04-16 10:47
Title: LUCAS Sprint 06 April-May
Category: Sprint, Agile, LUCAS
Tags:  Sprint, Agile, LUCAS
layout: post

  
  \newpage
---

These are the sprint archives/summaries of [Anthony Beck](http://orcid.org/0000-0002-2991-811X). Anthony is a part time (60% Full Time Equivalence (FTE)) researcher on the [Leverhulme Trust](http://www.leverhulme.ac.uk/) funded project [Sustaining Urban Habitats - an interdisciplinary approach](http://www.nottingham.ac.uk/research/groups/environmental-physics-and-design/leverhulme-project.aspx) led by [Prof Darren Robinson](http://www.nottingham.ac.uk/engineering/departments/abe/people/darren.robinson).

These documents represent an archive of the work undertaken by Ant. 

Unless stated otherwise these documents are released under a [CC0](https://creativecommons.org/choose/zero/) [(+BY)](http://www.dancohen.org/2013/11/26/cc0-by/). This means that it is essentially in the public domain and you can re-use it in an unfettered way. I would, however, appreciate, but not mandate, a reference.

# Sprint 06 13th April - 24th April 2015

Sprint Objectives:  

Get the sprint planning back on track. Easter and unanticipated tasks (repository paper/presentation for Darren) have eaten up a significant amount of time.

This sprint has the following sub-tasks:nottingham 


* PostGres repository
	* All O/S edina data in
	* Needs some more tinkering (brackets and speech marks in some of the OGR ingest - filter these out)
	* All command line based
	* All within a single Database with data separated into distinct schema
	* Derivatives produced 
* Thinking about workflow environment
	* [Talend](https://www.talend.com/)
	* [Knime](https://www.knime.org/)
	* [Taverna](http://www.taverna.org.uk/)
	* [Alteryx](http://www.alteryx.com/)
* Data requirements gathering
	* Looking at UrbanSim
* Big Data workshop
	* Thursday
	* follow ups
		* 20150506 Meeting with Philip Quinlan
* PhD summaries
	* an ontology based one??? 
	* Citygml construction/3d modelling for one of the Chinese cities? 
	* Geodata analytics and workflows to support urban and city simulation.
* [ESA EarthObservation science conference](http://www.eoscience20.org/)
	* Submit something
		* Heritage with Dave Cowley
		* LUCAS? - Fill something in for this.
* [AHRC - Cross-Disciplinary Research Networks](http://www.ahrc.ac.uk/Funding-Opportunities/Pages/Cross-Disciplinary-Research-Networks-Exploring-Emerging-Areas-of-Cross-Council-Enquiry-Highlight-Notice.aspx)
	* Open until end July 2015
	* Soundbites
		* We hope that the networking awards funded under the highlight will help to bring distinctive arts and humanities perspectives and approaches more centrally into these emerging fields of cross-disciplinary enquiry.
		* Looking to support networking activities that will open up new cross- and inter- disciplinary research agendas and develop new collaborations between arts and humanities researchers and other research and practice communities outside the arts and humanities
	* applications must demonstrate the following characteristics:
		* strong leadership from arts and/or humanities researchers as a part of the core team of investigators and the incorporation and integration of distinctive arts and humanities research perspectives and strengths into the core of the proposed research agenda for the networking activities;
		* a commitment to cross-disciplinary working across the boundaries between the arts and humanities and sciences (broadly defined), including evidence of engagement with researchers / practitioners in the relevant field(s) of science / technology in developing the networking proposal;
		* plans for significant participation by relevant researchers from the sciences and/or relevant fields of practice (e.g. technology development, medicine, engineering etc.) in the proposed networking activities;
		* address emerging areas, disciplines, technologies or issues where there has been relatively little research engagement to date between  the arts and humanities and the sciences and which involve a high degree of potential cross-disciplinary innovation and novelty.	
	* we are particularly keen to encourage applications addressing any of the following areas: 
		* Risk
		* Conflict, transnational organised crime or cyber- security
		* Cities / urbanisation/ urban Living / ‘smart’ cities
		* Valuing nature
		* Anti-microbial resistance (AMR)
		* Wellbeing
		* Emerging areas of science and technology, (including, for example, the Internet of Things, robotics and autonomous systems, synthetic biology, regenerative medicine, wearable technologies, etc.)
* Preparation for OS meeting Tuesday 28th
* Unanticipated
	* Grant application 0.5 days
	* Feedback on doucmentation about Warwick/Birmingham thing
	


## Tasks rolled over for the next sprint

* Thing to follow up: [Development of citizen based sensor systems](http://www.citi-sense.eu/) http://www.citi-sense.eu/
* [Automatic Statistician](http://www.automaticstatistician.com/research.php) by [Zoubin Ghahramani](http://mlg.eng.cam.ac.uk/zoubin/)

# Retrospective


## What went well?


## What have we learnt?

## What could we do better?


## What still puzzles us?



## What is blocking activity

Web site with Darren
Web-site david Aldred




# Task summary

## 20150506 Meeting with Philip Quinlan (ADAC) to discuss data anlytics and infrastructure

* We talked broadly about data analytics issues. 
	* lots of overlap in vision and approach (which is good). 
	* Both interested in getting a shared/callaborative frameworks (Ipython etc.)
* The general concensus was that ADAC and the Leverhulme project have a common purpose in terms of data analytics.
* There is a shift to providing data instances which can be queryable externally (a meeting will be arranged with IT to see what needs to be done to set this up for the project). 
* There are some issues that need resolving within the university in terms of ensuring that data analytics/transformation services have longevity and who provides the infrastructure to support this (for example OSMGB project services went down because the server was hacked). 
	*  It looks like the university is, in principle, prepared to wear the cost of providing OS infrastructure and where a service has been deemed worthy (i.e. people use it, it aligns with the strategy roadmap or has demonstrable impact) then resources can be made available to properly document the service so management and development overheads can be transferred.  
* We need to consider how ADAC can be written into future grants for Leverhulme

Philip has agreed to arrange a meeting with someone from IT who can provide advice about setting up project data infrastructre (thanks)

Ant - will provide support to ADAC in any way possible (feedback, supporting info etc.)


## Ordnance Survey meeting

Hi All,

In respect of the meeting on Tuesday next week I propose we meet 9:00 - 9:15 (I know Gavin may be a little late) and keep the agenda pretty flexible. Some of us haven't met before - my main aim is for us all to get to know each other and to establish some common ground for ongoing collaboration.

Initially Gavin will set the scene with a c. 20 minute overview of the Housing Stock Energy modelling at Nottingham.

I'm sure this will be followed up by discussion that covers things like data, workflows and requirements (Gavin and I talked about this today and in addition to things like remote sensing data we'd be interested in other 'value add' attributes which may not be formally exposed in MasterMap).

It looks like Darren (the PI) may have got the go ahead to establish Nottingham as a city data observatory. If this is confirmed then the aim is to collate and collect lots of data on Nottingham - multiple sensors, multiple surveys (physical, socio-economic etc) different models (CityGML etc.). I will present something on this.

Hopefully this should lead into discussions on PhD studentships, research synergies and collaborative opportunities. 

We have the room until 12 and Doreen needs to leave for a meeting at Kew by 12:30.

I think that's everything.

Really looking forward to meeting you all.

Best wishes

Ant




#
