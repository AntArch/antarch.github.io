---
title:  'DRAFT - Data repository for IEA project'
author: Anthony Beck
tags: TRAC
bibliography: references.bib
csl: harvard.csl
abstract: |
  
  [Professor Darren Robinson](http://www.nottingham.ac.uk/engineering/departments/abe/people/darren.robinson) from Nottingham University is co-leading *Subtask B: Occupant action models in residential buildings* as part of [International Energy Agency](http://www.iea.org/) (IEA) [Annex 66](http://www.annex66.org/). 
  
  There is a recognised need to collate and make available relevant research objects^[data, algorithms, publications, illustrations etc.] to the project stakeholders with the overarching goal of ensuring methodological transparency and scalability. These research objects will be made available through a *repository environment* with a supporting metadata system that will facilitate resource discovery and exploitation. Research objects should be accessed through a web-interface with a simple upload and download facility. 
  
  This document will be summarised into a slide deck with approximately ten slides.
  
  cd /home/arb/ownCloud/Nottingham/LUCAS/Sprints/Sprint03/20150331_RepositoryForDarren

  pandoc -f markdown -t latex -N -V geometry:margin=1in 20150331_RepositoryText.md 20150331_RepositoryAppendix.md 20150331_RepositoryRefs.md --filter pandoc-citeproc --latex-engine=xelatex --toc -o Text/20150331_Repository.pdf
  
  \newpage
...

\newpage

# [International Energy Agency](http://www.iea.org/) (IEA) [Annex 66](http://www.annex66.org/) Subtask B: *Occupant action models in residential buildings* 

[Professor Darren Robinson](http://www.nottingham.ac.uk/engineering/departments/abe/people/darren.robinson) from Nottingham University is co-leading *Subtask B: Occupant action models in residential buildings* as part of [International Energy Agency](http://www.iea.org/) (IEA) [Annex 66](http://www.annex66.org/). The Annex aims to set up a standard occupant behavior definition platform, establish a quantitative simulation methodology to model occupant behavior in buildings, and understand the influence of occupant behavior on building energy use and the indoor environment. Further context is provided below:

> Energy related occupant behavior in buildings, for example adjusting thermostat for comfort, switching lights, opening/closing windows, pulling up/down window blinds, and moving between spaces, is a key issue for building design optimization, energy diagnosis, performance evaluation, and building energy simulation due to its significant impact on real energy use and indoor environmental quality in buildings. However the influence of occupant behavior is under-recognized or over-simplified in the design, construction, operation, and retrofit of buildings. Occupant behavior is complex, stochastic and multi-disciplinary (Figure \ref{annex66fig1}). Having deep understanding of occupant behavior and being able to model and quantify its impact on use of building technologies and energy performance of buildings is crucial to design and operation of low energy buildings. Existing studies on occupant behavior, mainly from the perspective of sociology, lack in-depth quantitative analysis. There are over 20 groups all over the world studying occupant behavior individually. The occupant behavior models developed by different researchers are often inconsistent, with a lack of consensus in common language, in good experimental design and in modeling methodologies. Due to the complexity and the great district discrepancy of occupant behavior, it is prerequisite for researchers to work together to define and simulate occupant behavior in a consistent and standard way [@iea-ebc_annex_66_iea-ebc_2014].

![Relationship between occupants and buildings [@iea-ebc_annex_66_iea-ebc_2014]\label{annex66fig1}](http://annex66.org/images/introduction_1.png)

Subtask B: *Occupant action models in residential buildings* aims to address current inconsistencies in experimental design and the lack of availability of high quality data, modelling methodologies, model algorithms or source code. Coordination of efforts to ensure the above, avoiding replication and channeling effort where most needed are necessary. Models are supposed to be integrated into a coherent whole. Such a co-ordination effort requires a research repository. This document describes the nature and characteristics of such a repository.

# Initial brief

There is a recognised need to collate and make available relevant research objects^[data, algorithms, publications, illustrations etc.] to the project stakeholders with the overarching goal of ensuring methodological transparency and scalability. These research objects will be made available through a *repository environment* with a supporting metadata system that will facilitate resource discovery and exploitation. Research objects should be accessed through a web-interface with a simple upload and download facility. 

The metadata describing the research objects will be made available freely (under a [CC0 licence](https://creativecommons.org/choose/zero/)). This will support resource discovery. The research objects themselves will be made available under a licence that constrains their access and re-use. The exact terms of this licence need defining and legal confirmation (the purpose of this document). Constraint cases include:

1. Only communities who contribute to the repository are allowed to re-use the resources. Repository contribution includes:
	1. Addition of data
	1. Addition of algorithms and models
	1. Co-authorship of papers with a member who is in category 1 and 2^[I appreciate this is somewhat ambiguous. How can someone get access at this level without getting access to the data first?]
1. By attribution
	* All research object re-use should include an attribution^[this implies that the metadata should include a citation field for each research object]
1. For research use only (does this mean a *Non-Commercial* clause - and a specific statement about research use)

No stipulation has been made on other types of constraint^[I would argue that these constraining licences should not be used at all]:

* No Derivatives 
* Licensing of Derivatives (for example the [Creative Commons *share-a-like* clause](http://en.wikipedia.org/wiki/Share-alike))
* No Commercial use^[which demands a definition of what commercial use is (and in an academic context as to which academic activities are commercial and which aren't (I would argue that undergraduate teaching is now a commercial activity in the United Kingdom)))]

The initial aim is to build a *closed ecosystem* repository. You obtain access to the resources by making a contribution which can be used by members. This is seen as a short term catalyst to encourage the sharing of resource objects by the community. Such a closed ecosystem constrains access. To constrain access without resource leakage will require either:

* a specific licences
* a code of conduct 
* or both a specific licence and a code of conduct

Although a specific licence may be stipulated for the *closed ecosystem* the grant that supported the original data (or resource) acquisition may have pre-existing licence stipulations. These should be adhered to. However, resources can be released separately under different licences^[we do need legal advice on the practicalities of this]. Further, consideration should be given to licence incompatibilities that may inhibit the aggregation and derivation of content from different research resources.

Once a quantified critical mass has been reached then the whole ecosystem could be opened under more liberal licences as a platform to encourage extended research, development and collaboration.

A *closed ecosystem* requires some form of federated access in order to function. Access accreditation is therefore a requirement of the repository framework. 

In terms of data it is as yet unclear as to whether this is seen as a data preservation environment^[which will ensure the data is in a format and a facility that ensures access in perpetuity (which formally equates to a [maximum of 25 years](http://archive.icommons.org/articles/preserving-digital-heritage-for-perpetuity-or-at-least-for-the-next-25-years))], a data analysis platform^[which aggregates and materialises the data in a manner which streamlines downstream processing] or both.  This will become clearer when sufficient exemplar data is made available^[Darren: could I have some data please :-)]. However, two types of data have been posited:

* Longitudinal
	* Repeatable observations over a small number of subjects
	* *State* or *event* measurements on objects (indoor microclimate, outdoor micro(climate), adaptive controls, personel characteristics, presence activities, comfort.... )
* Transverse
	* Questionnaire based
	
Subject to data evaluation and a requirements analysis these data can be fitted into standard data models. It is likely a traditional Object Relational Model for the Longitudinal data and a triplestore for the transverse data. 

The outputs requested by Darren are:

* Sample licence agreement
* 20-30 minute presentation (for the end of March 2015)

This document is a by-product of this process.

\newpage

# Assumptions

Assumptions made during the preparation of this document

* There are finances in place to pay for an external repository (if necessary) or to fund the development of a project repository if necessary.
* That resource re-users within the *closed ecosystem* will not *leak* the resources into the public domain (formalised under a licence or code of conduct?).
* Contributers will come from different countries and be mainly, but not exclusively, from academic organisations. 

\newpage

# Background - repositories and the sharing of research resources

*Repositories* are now part of the academic lexicon. In the UK this is a reflection of the stances taken by Research Councils UK (RCUK), the Royal Society, the Engineering and Physical Sciences Research Council (EPSRC) and Horizon 2020. 

> Open inquiry is at the heart of the scientific enterprise. Publication of scientific theories – and of the experimental and observational data on which they are based – permits others to identify errors, to support, reject or refine theories and to reuse data for further understanding and knowledge. Science’s powerful capacity for self-correction comes from this openness to scrutiny and challenge [@royal_society_science_2012 p. 7].

The Royal Society’s report *Science as an open enterprise* [-@royal_society_science_2012] identifies how 21^st^ century communication technologies are changing the ways in which scientists conduct, and society engages with, science. The report recognises that ‘open’ enquiry is pivotal for the success of science, both in research and in society. This goes beyond open access to publications (Open Access), to include access to data and other research outputs (Open Data), and the process by which data is turned into knowledge (Open Science).

These concepts are deeply embedded within Horizon 2020. Specific themes are included within the programme to provide appropriate capacity [@hudson_open_2012; @_european_2014]: 

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

The implied vision is to make all outputs of Horizon 2020 openly accessible. Key to this are initiatives like *Zenodo* [@_zenodo_2014]: an FP7 funded repository framework developed by CERN. 

What is happening in academia is part of a broader trend - specifically in terms of *open data*:

>More than 40 countries—from every region of the world and at every stage of development—have established open data initiatives. These nations are opening up all kinds of data sets to promote economic development, spark innovation, and find ways to make government work better. India has released 3,500 data sets, mostly of agricultural information. Singapore has shared 8,600 data sets from 60 public agencies. The World Wide Web Foundation’s Open Data Index rates governments on 14 data-sharing metrics and in 2012 ranked the United States, Mexico, Singapore, the United Kingdom, and New Zealand as the top five most open governments..... The commitment to making data more open was re-affirmed at the June 2013 G8 summit through the Open Data Charter, which establishes “an expectation” that the default policy should be that all government data be published openly [@mckinsey_open_2013, p. 5].

Open data at a global level is a reality: the Open Knowledge Foundation’s Open Data Index [@open_knowledge_foundation_open_2013], and the Open Data Barometer [@the_web_foundation_the_open_data_institute_open_2013], published by the World Wide Web Foundation, provide an overview on the global state of open data. The global open data movement is as much characterised by the communities of practice surrounding data re-use and engagement as it is by the data itself [@government_digital_service_government_2013].  The recommendations from the Shakespeare review [-@shakespeare_shakespeare_2013] indicate that the amount of government Open Data, at least in the UK, is only going to grow. Reports within the collection 'Beyond Transparency' [@goldstein_beyond_2013] provide an overview of the communities of practice within the public sector. All reports describe the principles of open data: that it should be complete, timely, accessible, able to be processed by a machine, non-discriminatory, available without registration, non-proprietary, and free of any copyright or patent regulations. In addition Coleman refers to the “Three Laws of Open Government Data” [@goldstein_beyond_2013, p. 41]:

* If it can’t be spidered or indexed, it doesn’t exist.
* If it isn’t available in open and machine-readable formats, it can’t engage.
* If a legal framework doesn’t allow it to be repurposed, it doesn’t empower.

Open data has the potential to trigger a revolution in how governments think about providing services to citizens and how they measure their success: this produces societal impact. This will require an understanding of citizen needs, behaviours, and mental models, and  how to use data to improve services.  A McKinsey Global Institute report examines the economic impact of Open Data [@mckinsey_open_2013] and estimates that globally open data could be worth a minimum of $3 trillion annually. This report complements a previous McKinsey report on the impact of Big Data [@mckinsey_company_big_2011]. The expected global increase in demand for open data across all sectors is likely act as a vehicle to remove frictions to data release by governments and bureaucrats. 

From a pragmatic viewpoint the Open and Big data frameworks are still in their early stages and have yet to stabilise and mature. Finding data can be difficult as the quality of the description and discovery metadata is variable. In addition the importance and re-use constraints for data is also poorly documented (data.gov.uk has 16,504 datasets, important data can very easily be swamped). Underlying persistence can also be a problem: in Australia, the government recently pared down its datasets by a third, claiming that some were “junk,” and cleaned up others (e.g., it consolidated 200 files into a single dataset) [@_govt_2013]. Some data isn’t necessarily available in a format that’s easy to use, or in a state where it can be inserted straight into a production environment (it requires validation and enhancement). It is likely that the supporting frameworks will undergo significant changes in the short-term as developers provide feedback. This builds on Bracken's call for 'an evidence-based assessment of what people want or need' [@goldstein_beyond_2013, p. 273] so that services, frameworks and products can be effectively developed and delivered. 

As an ever larger amount of data is digitized and travels across organizational boundaries, there are a set of policy issues that will become increasingly important, including, but not limited to, privacy, security, intellectual property, and liability. Questions about the intellectual property rights attached to data will have to be answered: Who "owns" a piece of data and what rights come attached with a dataset? What defines "fair use" of data? What are the liability issues when data is re-used outside it's initial scope or use-case [@mckinsey_company_big_2011]. Hence, data licences are crucial to make such issues transparent.

Within academia the underlying rationale of Open Data is this: unfettered access to large amounts of ‘raw’ data enables patterns of re-use and knowledge creation that were previously impossible. The creation of a rich, openly accessible corpus of data introduces a range of data-mining and visualisation challenges, which require multi-disciplinary collaboration across domains (within and outside academia) if their potential is to be realised. An important step towards this is creating frameworks which allow data to be effectively accessed and re-used. The prize for succeeding is improved knowledge-led policy and practice that transforms communities, practitioners, science and society.

The need for such frameworks will be most acute in disciplines with large amounts of data, a range of approaches to analysing the data, and broad cross-disciplinary links. Such approaches cannot be undertaken within a single domain of expertise. This vision can only be built by openly collaborating with other scientists and building on shared data, tools and techniques. Open Science advocates opening access to data, and other scientific objects, at a much earlier stage in the research life-cycle than traditional approaches. Open Scientists argue that research synergy and serendipity occur through openly collaborating with other researchers (more eyes/minds looking at the problem). Of great importance is the fact that the scientific process itself is transparent and can be peer reviewed: as a result of exposing data and the processes by which these data are transformed into information, other researchers can replicate and validate the techniques. As a consequence, collaboration is enhanced and the boundaries between public, professional and amateur are blurred. 

The positions taken by Research Councils UK [-@royal_society_science_2012] and the EPSRC [-@epsrc_research_2014] on improving access to data are key catalysts for change. The EPSRC statement is particularly succinct, two of the principles are of particular importance: 

> * Published research papers should include a short statement describing how and on what terms any supporting research data may be accessed.
> * Where access to the data is restricted the published metadata should also give the reason and summarise the conditions which must be satisfied for access to be granted. For example ‘commercially confidential’ data, in which a business organisation has a legitimate interest, might be made available to others subject to a suitable legally enforceable non-disclosure agreement.

This has produced a simple economic issue – if research institutions can not demonstrate that they can manage research data in the manner required by the funding councils then they will become ineligible to receive grant funding from that council. The impact is that the majority of universities are now developing their own, or collaborating on communal, data repositories. Organisations like the Digital Curation Centre (DCC) in the UK are providing leadership and advice to academic organisations [for example @miller_5_2012].

## What is a repository

The Repository Support Project [@jisc_repositories_2013] described repositories as follows:

> A digital repository is a mechanism for managing and storing digital content. Repositories can be subject or institutional in their focus. Putting content into an institutional repository enables staff and institutions to manage and preserve it, and therefore derive maximum value from it. A repository can support research, learning, and administrative processes. Repositories use open standards to ensure that the content they contain is accessible in that it can be searched and retrieved for later use. The use of these agreed international standards allows mechanisms to be set up which import, export, identify, store and retrieve the digital content within the repository.

> Digital repositories may include a wide range of content for a variety of purposes and users. What goes into a repository is currently less an issue of technological or software ability, and more a policy decision made by each institution or administrator. Typically content can include research outputs such as journal articles or research data, e-theses, e-learning objects and teaching materials, and administrative data. Some repositories only take in particular items (such as theses or journal papers), whilst others seek to gather any credible scholarly work produced by the institution; limited only by each author's retained rights from publishers. However, some more complex objects (websites, advanced learning objects, 3D topographical representations and other data sets) do present a technological challenge.

Many view the primary function of a repository to store or archive resources and to facilitate discovery through metadata. There is a difference between storage and archiving. *Storage* can be any simple process that takes the resources as it stands and makes it available for others through the repository. *Archivation* is an active process that attempts to ensure that the resource is re-useable in the future. To a digital archivist standards, well documented formats, open formats and format migration are important concepts. 

Once stored the resource need a mechanism to be discovered. Each resource contains metadata (*data about data*) that can be used to describe any aspect of the resource. The discovery process is facilitated by standards and schemas - for example [Dublin Core](http://dublincore.org/) is a commonly used metadata schema and the Open Archives Initiative Protocol for Metadata Harvesting ([OAI-PMH](http://www.openarchives.org/pmh/)) is a protocol for sharing metadata. The sharing of metadata (normally under an open [CC0 licence](https://creativecommons.org/choose/zero/) licence) through technologies like OAI-PMH means that information about the data (including its storage location) can be shared between different harvesting environments. This is designed to increase *discovery*. *Domain repositories* can take, or *harvest* metadata from different *institutional* or *subject repositories*. When a potential end-user searches for resources via such a *domain repository* results can be displayed from different source repositories. This leads to improved discovery which should finally lead to re-use. *Re-use* is ultimately what repositories want to facilitate. More specifically they should facilitate the clear re-use of the research object in a mannner where the re-user understands:

* The licence under which the resource is shared
* Who and how to credit the provider of the resource
* The provenance of the resource
* The potential uses to which the resource may be put
* The constraints associated with the resource
* etc.

In the context of a data environment a data repository may not provide (or expose) the data in a manner which means it can be used directly within a workflow. Whilst some repositories provide API's to provide views over the data - the underlying formats and infrastructure may not be optimised for large-scale processing. This is more likely to be the case in an environment where the data has been archived - where longer-term preservation issues may have a negative impact on the ability to re-use data.

## Licences and waivers

Licences are fundamental to the successful re-use of content. Licences describe who can use a resource, what they can do with this resource and how they should reference any resource (if at all).

The Digital Curation Centre (DCC) summarise this situation well [@ball_how_2012]:

> The two most effective ways of communicating permissions to potential reusers of data are licences and waivers. A licence in this context is a legal instrument for a rights holder to permit a second party to do things that would otherwise infringe on the rights held. The first thing to note is that only the rights holder (or someone with a right or licence to act on their behalf) can grant a licence; it is therefore imperative that the intellectual property rights (IPR) pertaining to the data are established before any licensing takes place. The second thing to note is that while it is the nature of a licence to expand rather than restrict what a licensee can do, some licences are presented within contracts, and contracts can place additional restrictions on the licensee and indeed the licensor.

> A waiver, by contrast, is a legal instrument for giving up one’s rights to a resource, so that infringement becomes a non-issue. Again, only the entity that holds the rights (or someone with a right or licence to act on their behalf) can waive them. Note that a waiver does not authorise other parties to claim rights – as opposed to freedoms – they did not previously have.

Two lead organisations have developed legal frameworks for content licensing, [Creative Commons (CC)](https://creativecommons.org/) and [Open Data Commons (ODC)](http://opendatacommons.org/). Until the release of [CC version 4](https://wiki.creativecommons.org/4.0), published in November 2013, the CC licence did not cover data. Between them, CC and ODC licences can cover all forms of digital work.

At the top level the licences are permissive public domain licences (CC0 and PDDL respectively) that impose no restrictions on the licensees use of the resource. *‘Anything goes’* in a public domain licence: the licensee can take the resource and adapt it, translate it, transform it, improve upon it (or not), package it, market it, sell it, etc. Constraints can be added to the top level licence by employing the following clauses:

* BY – By attribution: the licensee must attribute the source.
* SA – Share-alike: if the licensee adapts the resource, they must release the adapted resource under the same licence.
* NC – Non commercial: the licensee must not use the work within a commercial activity without prior approval. Interestingly, in many area of the world, the use of material in university lectures may be considered a commercial activity. The non-commercial restriction about the nature of the activity, not the legal status of the institution doing the work.
* ND – No derivatives: the licensee can not derive new content from the resource.

Each of these clauses decreases the ‘open-ness’ of the resource. In fact, the NC and ND clause are not intrinsically open (they restrict both who can use and what you can do with the resource). These restrictive clauses have the potential to produce license incompatibilities which may introduce profound problems in the medium to long term. This is particularly relevant to the SA clause. Share-alike means that any derived output must be licensed under the same conditions as the source content. If content is combined (or mashed up) – which is essential when one is building up a corpus of resources – then content created under a SA clause can not be combined with content that includes a restrictive clause (BY, NC or ND) that is not in the source licence. This licence incompatibility has a significant impact on the nature of the data commons. It has the potential to fragment the data landscape creating pockets of knowledge which are rarely used in mainstream analysis, research or policy making. This will be further exacerbated when automated data aggregation and analysis systems become the norm^[which are implied as expected in this project]. A permissive licence without clauses like Non-commercial, Share-alike or No-derivatives removes such licence and downstream re-user fragmentation issues.

For completeness, specific licences have been created for Open Government Data. The [UK Government Data Licence for public sector information](http://www.nationalarchives.gov.uk/doc/open-government-licence/version/2/) is essentially an open licence with a BY attribution clause.

It is also worth reading the [guidelines of The Open Data Institute](http://theodi.org/guides/publishers-guide-open-data-licensing) which illustrate the different types of data object and the different re-use scenarios available. There is a post advocating [ccZero+ by Dan Cohen](http://www.dancohen.org/2013/11/26/cc0-by/). This post recognises that no one will police attribution and removes the *constraint* to attribute and replaces it with a *suggestion* to attribute. However, impact tracking may mean that the BY attribution clause becomes a default for academic deposition. The issue of impact tracking in an environment with a whole range of different research objects is advocated by the altmetrics community [@priem_altmetrics:_2011].

Bespoke licences can be problematic - they tend not to map to national or international licence schemes. There is the possibility that as this community wants to operate in a *closed ecosystem* then a bespoke licence may be required to keep the ecosystem closed. Bespoke licences can bring in unintended issues when conflated with other data and, if using automated data aggregation systems, the data might simply be ignored due to licence incompatibilities.  

For example, the [Archaeology Data Service (ADS)](http://archaeologydataservice.ac.uk/) uses its own [bespoke licence](http://archaeologydataservice.ac.uk/advice/termsOfUseAndAccess) (see Appendix 1). The ADS has been in existence since 1995 prior to the consolidation of many of the widely adopted 'open' licences. Resources under the ADS licence can only be used for teaching, learning, and research purposes. This is the basis of their *constraint*. Of particular concern is their use of the NC clause and possible use of the ND clause (depending on how you interpret the licence). Interestingly, policy changes mean that the use of data under the bespoke ADS licence becomes problematic if university teaching activities are determined to be commercial. It is arguable that the payment of tuition fees represents a commercial activity. If this is true then resources released under the ADS licence can not be used within university teaching which is part of a commercial activity. Hence, the policy change in student tuition and university funding has an impact on the commercial nature of university teaching which has a subsequent impact on what data or resources universities are licensed to use. Whilst it may never have been the intention of the ADS to produce a licence with this potential paradox, it is a problem when bespoke licences are developed, even if they were originally perceived to be relatively permissive licences. In September 2014 the *preamble* to the *terms* of the ADS licence were changed to indicate that commercial useage was acceptable. Unfortunately the *preamble* is not the legal part of the document. Hence, there is still ambiguity in the legal part of the document. 

## Concerns about opening up data, and responses which have proved effective

Coleman [@goldstein_beyond_2013] identified that during the early stages of transition within UK government to open data there was fricition. This was split between social cultures within government (secretive and bureaucratic) and 'progressive attempts by governments to exploit the monetization of state data'. Whilst this problem still remains the benefits of open data are becoming apparent to the full stakeholder chain. This is reflected int eh scope of the open data movement.

Christopher Gutteridge (University of Southampton) and Alexander Dutton (University of Oxford) have collated a Google doc entitled [‘Concerns about opening up data, and responses which have proved effective‘](https://docs.google.com/document/d/1nDtHpnIDTY_G32EMJniXaOGBufjHCCk4VC9WGOf7jK4/edit#heading=h.2hfedqqfbl6k). This document describes a number of concerns commonly raised by academic colleagues about increasing access to data.

Such friction is an ongoing problem that will be resolved by policy statements from governments and funders (such as those from EPSRC, RCUK and Horizon 2020) and changes in operational norms. 

## The data life-cycle

![A view of the Research Data life-cycle ([provided by Helen Morgan and Nadine Davidson-Wall from the University of Queensland](http://guides.library.uq.edu.au/research-data-management))\label{rd_life-cycle}](http://s3.amazonaws.com/libapps/customers/720/images/Life_Cycle_Diagram.jpg)

It is assumed, subject to ethical and IP considerations, that within a generation that most academic projects will be mandated to deposit their data in a Data repository^[however, the timing of deposition is uncertain and this does not mean that backlog data will be deposited]. It is further assumed that an Open Data licence is likely to be the default for such data.

Most academics see data sharing as a specific stage in the research data life-cycle (for example see Figure \ref{rd_life-cycle}). Such sharing tends to occur at the end of a project as part of an archiving and exposure process. Whilst, many academics are *expected* to archive their data, few do. Up until recently there has been little incentive to do so. The policy changes instituted by some research councils are likely to see a change in this situation. Even so, a significant amount of data will exist in a *limbo*: the community is aware it exists but can not get access to it. This has created a paucity of data - one approach to alleviate this is to provide access to data at a much earlier stage in the research life-cycle. 

Providing access to data earlier in the research life-cycle is a significant change in research practice. It is likely that those who contribute would like to ensure that the data they have spent many hours collecting and refining is not misappropriated and whilst others can gain insight from the data that they have the ability to exploit the data effectively **and** are credited appropriately by others. An open licence at such an early stage would mean that contributors got credit for their contribution but might not maximise their personal impact (the data is cited but the data collectors are not invited to be co-authors on a resulting high impact *Nature paper*). In this scenario the research process as a whole benefits but there is a disincentive for those people who collect high quality data to share it so early. 

An alternative solution is a members club. A *closed ecosystem* in which members get access to critical data, algorithms and other resources at an earlier stage in the research life-cycle for the common good of the group. The *benefits* of sharing are access to the *cumulative resources* shared by the group with the aim of increasing *research output* accordingly. The aim is to increase altruistic data sharing by excluding those members who do not contribute to the community (through agreed norms). 

This has a number of benefits and reduces some risks (assuming there is trust in the membership network). Early release of data could have a fundamental impact on the data itself: the point of such a system in this context is to **re-use** data and other resources. Although, this point may seem simple - this is not the primary purpose of most repositories. Most repositories simply deal with 'ticking the box' that say the data has been deposited. Data which is *actively re-used* by an engaged user community should result in more rapid feedback on documentation and quality issues. The key point is this feedback occurs whilst there are people paid on the project to improve the data. This in better data and metadata which ultimately leads to better discovery and better research.

# A *closed ecosystem* repository

## Accreditation frameworks

A *closed ecosystem* requires some form of federated access in order to function. Access accreditation is therefore a requirement of the repository framework. The level of access may need fine-tuning (from individuals to groups). This in turn needs an individual, or a committee, to approve access when new users of groups want to use the resources. This is likely to have both a time and cost overhead. 

## Early research life-cycle data sharing exemplar

Data sharing early in the research life-cycle could represent a risk. The challenge is to minimise the risk while maximising the output. The following life-cycle is 

* Closed ecosystem resource ingest
	* resource metadata created and publicly exposed (harvested by other repositories, thereby advertising the community)
	* resource citation created
	* embargo period defined (i.e. period after which the resource is released^[This makes much more sense if the previous assumptions are taken: It is assumed, subject to ethical and IP considerations, that within a generation that most academic projects will be mandated to deposit their data in a Data repository. It is further assumed that an Open Data licence is likely to be the default for such data.])
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

The above scenario allows research objects to be used within the community and to be cited but, dependent on the nature of the waivers, does not allow the resources to be leaked outside the community. 

Whatever approach the community determine will need documenting. Any changes to this would need mandating by a quorum in the community.

Policing this is a different matter. 

## Breaking down the walls of the *closed ecosystem*

The argument for the *closed ecosystem* is to build a community based upon a common purpose. It should be hoped that there will become a point in time when this community has coalesced and does not need a *closed ecosystem* to function effectively. In fact, some of the licence constraints required to institute a *closed ecosystem* described above may have a negative impact on on-going research programmes (particularly if policy structures change). It is at this point that an exit-strategy is required.

\newpage

# Recommendations

## Repository

The repository must have the following characteristics:

* User accreditation
	* With users from multiple institutions - not exclusively academic
* OAI-PMH harvesting

Ideally the repository should have the following characteristics:

* A data API
* Bulk data ingest facilities
* Incorporation of common collaboration environments (i.e. GitHub and DropBox)
* Citation snippets (in an open citation format such as Bibtex)
	* to encourage the correct citation of the resources using bibliographic management packages
* DOI minting

### Repository shortlisting

**Bespoke or Institutional repositories**

Bespoke repositories (likely to be based on an open source framework) have a high management and cost overhead and will require the hiring of skilled personel to *'reinvent the wheel'*.  Most institutional repositories simply don't yet exist, are immature or cater exclusively on the needs of the host institution (as opposed to a broad consortium from different, or no, institutions). Neither bespoke or institutional repositories tend to have robust bulk ingest or collaborations tools (beyond that provided by the source application) and may not have DOI minting capabilities. 

**Independent repositories**

There are a number of independent repositories of which a subset allow *closed ecosystems*. Two of the main repositories are:

[**Figshare**](http://figshare.com/)

> Figshare is an online digital repository where researchers can preserve and share their research outputs, including figures, datasets, images, and videos.[1] It is free to upload content and free to access, in adherence to the principle of open data. Figshare is a portfolio company of Digital Science, operated by Macmillan Publishers.

[**Zenodo**](https://zenodo.org/)

> Zenodo is an open dependable home for the long-tail of science, enabling researchers to share and preserve any research outputs in any size, any format and from any science.

Useful links:

* [Zenodo policies](https://zenodo.org/policies)
* [Zenodo FAQs](https://zenodo.org/faq)
* [Zenodo features](https://zenodo.org/features)
* [Figshare FAQs](http://figshare.com/faqs)
* [Figshare features](http://figshare.com/features)

### Repository recommendation

I would recommend that data from the IEA is held in an independent repository rather than an institutional or bespoke repository. My preference would be for Zenodo. 

Zenodo was funded through [OpenAIRE](https://www.openaire.eu/) in FP7. Zenodo, or a product derived from Zenodo, will become part of the Horizon 2020 environment and as such it is something that the IEA consortium should engage with. It also supports EU wide approaches. Zenodo is free (for deposition and re-use for open and closed data). [Figshare has individual and institutional pricing](http://figshare.com/pricing). This may become complex when sharing data between multiple collaborators.  The modes of accreditation (for example Google, Twitter, ORCID, OpenAIRE^[I would recommend [ORCID](http://orcid.org/0000-0002-2991-811X)]) in Zenodo are broader than FigShare. The Open and Closed community element is also more flexible and is not made unduly complex with a pricing infrastructure. With Horizon 2020 backing it is likely that Zenodo will see greater innovation (for example automated metadata creation is already implemented). Zenodo integrates with GitHub and DropBox and is actively developing bulk metadata ingest capabilities. 

Figshare has the benefit of being *at market* for a longer period (more established institutional links) and in accepting larger file uploads (5gb as opposed to 2gb). These upload values are likely to change.

## Licences (subject to legal verification)

Licences are open to debate. There is an argument that if data is made available to peers at an early stage in the research life-cycle it has not been formally released. It is shared within a broader research community  Hence, a potential *Code of Conduct* has been included below.

In current frameworks most data is viewed for deposit at the end of the *research data life-cycle*. Licensing may be mandated by the host research institution or funding body - there can be some latitude in this in terms of licence constraints but the section on licences details the pros and cons. Once data has reached this stage then it is recommended that a CC-BY or ODbL licence is adopted. 

However, this community is established in order to make data available at an early stage in the research process to facilitate collaboration. 

### Potential code of conduct text (based on the Archaeology Data Service text in the appendix)

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


### Bespoke licence clauses to negate resource reproduction

Based on the [RSPB](https://www.rspb-images.com/pages/terms.htm):

The reproduction by whatever means of the whole or any part of any data is strictly forbidden without the specific written permission of the 'Owner'. You must inform the 'Owner' of your proposals as to when and how data is intended to be used. The 'Owner' will then consider whether to grant a licence and, if so, on what terms.

No reproduction rights are granted by virtue of delivery of data unless expressly indicated. Your right to reproduce data arises only if 

1. licence terms are agreed and 
1. our invoice relating to the grant of such right is fully paid. 

Any reproduction outside the terms of any licence constitutes an infringement of copyright and a breach of this Agreement entitling the 'Owner' to rescind and claim damages. You must indemnify the 'Owner' in respect of any claims, damages, costs or expenses we incur arising from any reproduction of any data supplied to you.

You must satisfy yourself that all necessary rights, releases or consents which may be required for reproduction are obtained and that the use of any data is not obscene, indecent, libellous or unlawful. We make no claim or warranty with regard to your use of content, names, text, people, trademarks or copyright material depicted in any data and you will indemnify us in respect of any claims, damages, costs or expenses we incur arising from the use of any data supplied to you.

Reproduction rights (if granted), unless otherwise agreed in writing are 

1. subject to these terms and conditions and any terms and conditions set out in the delivery note and licence, 
1. strictly limited to the use, period of time and territory stated in the licence, 
1. personal to you and not assignable by you to any third party,
1. digital and analogue reproduction are granted and charged as separate licences,

#### Licence revoking

Legal advice should be sought about the implications of revoking the licences either when the group would like ALL resources to be publically available (i.e. it has achieved its goal) or when the research object is made available under a more open licence due to a funder constraint. 

## Presentation

If the content of this document adequately details the scenario then it will be whittled down to an image focussed presentation.

