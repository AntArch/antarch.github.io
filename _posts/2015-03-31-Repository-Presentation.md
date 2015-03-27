---
Date: 2015-03-31 10:47
title:  'IEA - Annex 66 - Subtask B'
author: Anthony Beck for Darren Robinson
layout: post
Category: academic, repository
Tags:  academic, repository
bibliography: references.bib
csl: harvard.csl
abstract: |
  
  Short abstract:
    This document has been written in [CommonMark](http://commonmark.org/): an unambiguous implementation of Markdown for scholarly writing.
    
  cd /home/arb/ownCloud/Nottingham/LUCAS/Sprints/Sprint03/20150331_RepositoryForDarren
    
  pandoc -t html5 --template=Presentation/template-revealjs.html --standalone --section-divs --variable theme="nightAnt" --variable transition="slide" 20150331_RepositoryPresentation.md --filter pandoc-citeproc -o Presentation/20150331_Repository.html
  
  pandoc -t odt --standalone --section-divs 20150331_RepositoryPresentation.md --filter pandoc-citeproc -o Presentation/20150331_Repository_doc.odt
  
  pandoc -t html --standalone --section-divs 20150331_RepositoryPresentation.md --filter pandoc-citeproc -o Presentation/20150331_Repository_html.html
  
  pandoc -f markdown -t latex -N -V geometry:margin=1in 20150331_RepositoryPresentation.md --filter pandoc-citeproc --latex-engine=xelatex --toc -o Presentation/20150331_Repository_pdf.pdf
  
  \newpage
---

# Background

#

## 

> Open inquiry is at the heart of the scientific enterprise..... Science’s powerful capacity for self-correction comes from this openness to scrutiny and challenge.

*Science as an open enterprise* [@royal_society_science_2012 p. 7].


## Slide notes

The Royal Society’s report *Science as an open enterprise* [-@royal_society_science_2012] identifies how 21^st^ century communication technologies are changing the ways in which scientists conduct, and society engages with, science. The report recognises that ‘open’ enquiry is pivotal for the success of science, both in research and in society. 

## 

![@open_science_does_not_equal_open_access_2013](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7c/Open_Science_Does_Not_Equal_Open_Access.svg/1024px-Open_Science_Does_Not_Equal_Open_Access.svg.png)

## slide notes

This goes beyond open access to publications (Open Access), to include access to data and other research outputs (Open Data), and the process by which data is turned into knowledge (Open Science).

## 

These concepts are deeply embedded within Horizon 2020.

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/zenodo.png)

Which has themes to provide capacity and capability

## slide notes

Specific themes are included within the programme to provide appropriate capacity [@hudson_open_2012; @_european_2014]: 

* Development of European Research Infrastructures (RIs)
	* Developing pan-European RIs (and regional potential)
	* Integrating and opening national RIs of pan-EU interest
	* Development, deployment & operation of e-Infrastructures
* Reinforcing the RI innovation potential & their human capital
	* Promoting the innovation potential of RI
	* Strengthening human capital
* Supporting consistency / efficiency of MSs & EU RI policies
	* Strengthening the EU RI policy
	* Strategic international cooperation

and capability:

* Building the “digital ERA” for all researchers
	* Data-centric science and engineering
	* Computational infrastructure (HPC, grids, clouds, software)
	* Research and education networks
	* Virtual research communities and e-science

The implied vision is to make all outputs of Horizon 2020 openly accessible. 

## Open Government

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/IncreasingContent.png)

## slide notes

The Shakespeare review [-@shakespeare_shakespeare_2013] indicate that the amount of government Open Data, at least in the UK, is only going to grow.

Open data has the potential to trigger a revolution in how governments think about providing services to citizens and how they measure their success: this produces societal impact. This will require an understanding of citizen needs, behaviours, and mental models, and  how to use data to improve services.  A McKinsey Global Institute report examines the economic impact of Open Data [@mckinsey_open_2013] and estimates that globally open data could be worth a minimum of $3 trillion annually. 

## 

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/EvidenceBasedDecisionMaking.png)

## slide notes

Within academia the underlying rationale of Open Data is this: 

* unfettered access to large amounts of ‘raw’ data enables patterns of re-use and knowledge creation that were previously impossible. 
* The creation of a rich, openly accessible corpus of data introduces a range of data-mining and visualisation challenges, which require multi-disciplinary collaboration across domains (within and outside academia) if their potential is to be realised. 
* An important step towards this is creating frameworks which allow data to be effectively accessed and re-used. 
* The prize for succeeding is improved knowledge-led policy and practice that transforms communities, practitioners, science and society

# The challenge

> If open is so great then where is the data?

#

##

![A view of the Research Data life-cycle ([provided by Helen Morgan and Nadine Davidson-Wall from the University of Queensland](http://guides.library.uq.edu.au/research-data-management))\label{rd_life-cycle}](http://s3.amazonaws.com/libapps/customers/720/images/Life_Cycle_Diagram.jpg)

## Slide notes

* Most academics see data sharing as a specific stage in the research data life-cycle. 
* Such sharing tends to occur at the end of a project as part of an archiving and exposure process. 
* Whilst, many academics are *expected* to archive their data, few do. 
	* Up until recently there has been little incentive to do so. 
* The policy changes instituted by some research councils are likely to see a change in this situation. 
* Even so, a significant amount of data will exist in a *limbo*: the community is aware it exists but can not get access to it. 
* This has created a paucity of data - one approach to alleviate this is to provide access to data at a much earlier stage in the research life-cycle. 

## 

![@early_lifecycle_sharing_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Early_Research_Lifecyle_Resource_Exposure_Via_A_Closed_Ecosystem.svg/587px-Early_Research_Lifecyle_Resource_Exposure_Via_A_Closed_Ecosystem.svg.png)

## slide notes

* Providing access to data earlier in the research life-cycle is a significant change in research practice. 
* It is likely that those who contribute would like to ensure that the data they have spent many hours collecting and refining is not misappropriated and whilst others can gain insight from the data that they have the ability to exploit the data effectively **and** are credited appropriately by others. 
* An open licence at such an early stage would mean that contributors got credit for their contribution but might not maximise their personal impact (i.e. data cited - but the data collectors are not co-authors on the *Nature paper*).
	* The code of conduct *should* resolve this professionally. 
	* None of this can be enforced!
* In this scenario the research process as a whole benefits but there is a disincentive for those people who collect high quality data to share it so early. 
* An alternative solution is a members club. 
* A *closed ecosystem* in which members get access to critical data, algorithms and other resources at an earlier stage in the research life-cycle for the common good of the group. 
* The *benefits* of sharing are access to the *cumulative resources* shared by the group with the aim of increasing *research output* accordingly. 
* The aim is to increase altruistic data sharing by excluding those members who do not contribute to the community (through agreed norms). 

## Short-term assumptions

* Within a generation academics mandated to deposit their data in a repository by funders (subject to ethical and IP considerations)
	* The timing of deposition is uncertain (due to an exclusive exploitation period)
	* This does not mean that backlog data will be deposited
* An Open Data licence (probably CC-BY) is the likely default.

# Key components

# 

## Community

![@trust_miemis_2010](https://farm5.staticflickr.com/4100/4757399524_6514646c1d_z_d.jpg)

## slide notes

* Shared norms. 
* An agreed code of conduct

## 

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/ResearchRepositories.png)

## slide notes

* A digital repository is a mechanism for managing and storing digital content. 
* Repositories can be non-discrimatory, subject or institutional in their focus. 
* Putting content into an institutional repository enables staff and institutions to manage and preserve it, and therefore derive maximum value from it. 
* A repository can support research, learning, and administrative processes. 
* Repositories use open standards to ensure that the content they contain is accessible in that it can be searched and retrieved for later use.
* The use of these agreed international standards allows mechanisms to be set up which import, export, identify, store and retrieve the digital content within the repository.

## 

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/DataRepositoryArchiveRepository.png)

## slide notes


* Many view the primary function of a repository to store or archive resources and to facilitate discovery through metadata. 
* There is a difference between storage and archiving. *Storage* can be any simple process that takes the resources as it stands and makes it available for others through the repository. 
* *Archivation* is an active process that attempts to ensure that the resource is re-useable in the future. 
* To a digital archivist standards, well documented formats, open formats and format migration are important concepts. 

##

![[Project core](http://project.core.ac.uk/)](http://project.core.ac.uk/files/core_diagram5.png)

## slide notes

Once stored the resource need a mechanism to be discovered: 

* Each resource contains metadata (*data about data*) that can be used to describe any aspect of the resource. 
* The discovery process is facilitated by standards and schemas - for example [Dublin Core](http://dublincore.org/) is a commonly used metadata schema and the Open Archives Initiative Protocol for Metadata Harvesting ([OAI-PMH](http://www.openarchives.org/pmh/)) is a protocol for sharing metadata. 
* The sharing of metadata (normally under an open [CC0 licence](https://creativecommons.org/choose/zero/) licence) through technologies like OAI-PMH means that information about the data (including its storage location) can be shared between different harvesting environments. 
* This is designed to increase *discovery*. 
	* When a potential end-user searches for resources via such a *domain repository* results can be displayed from different source repositories. 
* *Re-use* is ultimately what repositories want to facilitate. More specifically they should facilitate the clear re-use of the research object in a mannner where the re-user understands:

	* The licence under which the resource is shared
	* Who and how to credit the provider of the resource
	* The provenance of the resource
	* The potential uses to which the resource may be put
	* The constraints associated with the resource
	* etc.


* In the context of a data environment a data repository may not provide (or expose) the data in a manner which means it can be used directly within a workflow. 
* Whilst some repositories provide API's to provide views over the data - the underlying formats and infrastructure may not be optimised for large-scale processing. 
* This is more likely to be the case in an environment where the data has been archived - where longer-term preservation issues may have a negative impact on the ability to re-use data.

## Repositories are not analytics environments

They are not designed to query all data in advance of analysis:

* In the context of a data environment a data repository may not provide (or expose) the data in a manner which means it can be used directly within a workflow. 
* Whilst some repositories provide API's to provide views over the data - the underlying formats and infrastructure may not be optimised for large-scale processing. 
* This is more likely to be the case in an environment where the data has been archived - where longer-term preservation issues may have a negative impact on the ability to re-use data.

##

![@@analytics_and_workflow_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3c/Analytics_and_Workflow_platforms.svg/800px-Analytics_and_Workflow_platforms.svg.png)

##

![@bpm_workflow_beck_2013](https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Business_Process_Modelling_Workflow_Schematic.svg/1000px-Business_Process_Modelling_Workflow_Schematic.svg.png)

## 

![Summary of ADS terms and conditions. A textual version can be found [here](http://archaeologydataservice.ac.uk/advice/termsOfUseAndAccess/TermsAndConditionsSummary)](http://archaeologydataservice.ac.uk/attach/termsOfUseAndAccess/terms_and_conditions.jpg)

## slide notes

* A licence in this context is a legal instrument for a rights holder to permit a second party to do things that would otherwise infringe on the rights held. 
* A waiver, by contrast, is a legal instrument for giving up one’s rights to a resource, so that infringement becomes a non-issue. 
	* Note that a waiver does not authorise other parties to claim rights – as opposed to freedoms – they did not previously have.

Two lead organisations have developed legal frameworks for content licensing:

* [Creative Commons (CC)](https://creativecommons.org/) and 
* [Open Data Commons (ODC)](http://opendatacommons.org/). 

Until the release of [CC version 4](https://wiki.creativecommons.org/4.0), published in November 2013, the CC licence did not cover data. Between them, CC and ODC licences can cover all forms of digital work.

## Licence constraints

Constraints can be added to the top level licence by employing the following clauses:

* BY – By attribution: the licensee must attribute the source.
* SA – Share-alike: if the licensee adapts the resource, they must release the adapted resource under the same licence.
* NC – Non commercial: the licensee must not use the work within a commercial activity without prior approval.
* ND – No derivatives: the licensee can not derive new content from the resource.

---

Restrictive clauses have the potential to produce license incompatibilities - 

* CC-BY-SA can not be combined with CC-BY-SA-NC
* CC-BY-NC should not be combined with CC-BY-SA (what happens to the NC?)

## 

![Flickr licences](https://upload.wikimedia.org/wikipedia/commons/thumb/1/18/Flickr_license_types.svg/600px-Flickr_license_types.svg.png)

## 

![@accreditation_frameworks_beck_2015](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ee/Accreditation_Frameworks.svg/905px-Accreditation_Frameworks.svg.png)

## slide notes

* A *closed ecosystem* requires some form of federated access in order to function. 
* Access accreditation is therefore a requirement of the repository framework. 
* The level of access may need fine-tuning (from individuals to groups). 
* This in turn needs an individual, or a committee, to approve access when new users of groups want to use the resources. 
	* This is likely to have both a time and cost overhead. 

# Recommendations


#

## Proposed lifecycle

* Closed ecosystem resource ingest
	* resource metadata created and publicly exposed (harvested by other repositories, thereby advertising the community)
	* resource citation created
	* embargo period defined (i.e. period after which the resource is released)
		* This needs a time frame establishing
	* resource provided with a licence
		* waiver provided for the members while under embargo
		* Under embargo licence would need defining (can be open but data not shared - demonstrating intent)
		* the post embargo licence should be defined (default CC-BY)
	* members (all, individuals or groups) are given access to the data
* Post embargo the following occurs automatically:
	* the licence is changed to an open licence
	* a DOI is minted
	* the citation details are updated

## Repository

![](https://dl.dropboxusercontent.com/u/393477/ImageBank/zenodo.png)

[Zenodo short video - 3 minutes](https://dl.dropboxusercontent.com/u/393477/Temp/ZenodoUpload.webm)
[Zenodo long video - 6 minutes](https://dl.dropboxusercontent.com/u/393477/Temp/ZenodoOverview.webm)

## slide notes

* Bespoke repositories (likely to be based on an open source framework) have a high management and cost overhead and will require the hiring of skilled personel to *'reinvent the wheel'*.  
* Most institutional repositories simply don't yet exist, are immature or cater exclusively on the needs of the host institution (as opposed to a broad consortium from different, or no, institutions). 
* Neither bespoke or institutional repositories tend to have robust bulk ingest or collaborations tools (beyond that provided by the source application) and may not have DOI minting capabilities. 

Why Zenodo over figshare:

* Zenodo was funded through [OpenAIRE](https://www.openaire.eu/) in FP7. 
* Zenodo is free (for deposition and re-use for open and closed data). 
	* [Figshare has individual and institutional pricing](http://figshare.com/pricing). This may become complex when sharing data between multiple collaborators.  
* The modes of accreditation (for example Google, Twitter, ORCID, OpenAIRE) in Zenodo are broader than FigShare. 
* The Open and Closed community element is also more flexible and is not made unduly complex with a pricing infrastructure. 
* With Horizon 2020 backing it is likely that Zenodo will see greater innovation (for example automated metadata creation is already implemented). 
* Zenodo integrates with GitHub and DropBox and is actively developing bulk metadata ingest capabilities. 

## Licence

Proposed a [CC-BY licence](http://creativecommons.org/licenses/by/4.0/) and embargo period:

***You are free to***:

**Share** — copy and redistribute the material in any medium or format
**Adapt** — remix, transform, and build upon the material for any purpose, even commercially.

The licensor cannot revoke these freedoms as long as you follow the license terms.

***Under the following terms:***

**Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

No additional restrictions — You may not apply legal terms or technological measures that legally restrict others from doing anything the license permi


## Code of conduct

By using the the embargoed resources in this collection you are free to:

* Use - use material for learning, teaching and research (including commercial purposes)
* Adapt - remix, transform, and build upon the material for learning, teaching and research (including commercial purposes)

Under the following terms:

* Acknowledge, in any publication the original depositors.
* If you remix, transform, or build upon material, you must deposit your contributions to this community.

You cannot:

* Share - copy and redistribute the material in any medium or format

Notes:

* By teaching we mean directed teaching undertaken with a designated tutor in a formal setting.
* By learning we mean self-directed study, whether or not attached to an educational institution.
* By research we mean any work undertaken for the advancement of knowledge. Such work may be commercially sponsored, funded by academic bodies or learned societies, or it may be unsupported. 

# Required feedback

## Repository platform

Zenodo offers the functionality we need (accreditation, different licences, different exposure (private, public and embargoed) and DOIs), is free at the point of use and is likely to be around for a long time. The metadata used could be richer - but metadata completion is a recognised barrier to submission. 

---

* Is it agreed to use this platform?
* If other platforms are suggested:
	* What functions should they have?
	* How do we evaluate?

## Licence type

The recommendation is for CC-BY with an embargo period and code of conduct for *member* access.

---

* Is it agreed to use this approach?


## Analytics Platform(s)

Repositories will facilitate storage, exposure, discovery and in some ways re-use. They do not provide extract, cleanse, transform, enrich, integrate, mining or analytics capabilities.

---

* There is a need to understand the community requirements of extract, cleanse, transform, load and analytics.

##

# References 

Cited:
