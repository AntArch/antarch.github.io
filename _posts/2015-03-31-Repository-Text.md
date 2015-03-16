Date: 2015-03-31 10:47
Title: Data repository for IEA project
Category: academic, repository
Tags:  academic, repository

---
title:  'DRAFT - Data repository for IEA project'
author: Anthony Beck
tags: TRAC
bibliography: references.bib
csl: harvard.csl
abstract: |
  
  [Professor Darren Robinson](http://www.nottingham.ac.uk/engineering/departments/abe/people/darren.robinson) from Nottingham University is the lead on the data management theme of a project funded by the [International Energy Agency](http://www.iea.org/) which commences at the end of March 2015.
  
  There is a recognised need to collate and make available relevant research objects^[data, algorithms, publications, illustrations etc.] to the project stakeholders with the overarching goal of ensuring methodological transparency and scalability. These research objects will be made available through a *repository environment* with a supporting metadata system that will facilitate resource discovery and exploitation. Research objects should be accessed through a web-interface with a simple upload and download facility. 
  
  
  
  \newpage
...

\newpage

# Scope

[Professor Darren Robinson](http://www.nottingham.ac.uk/engineering/departments/abe/people/darren.robinson) from Nottingham University is the lead on the data management theme of a project funded by the [International Energy Agency](http://www.iea.org/) which commences at the end of March 2015. 

There is a recognised need to collate and make available relevant research objects^[data, algorithms, publications, illustrations etc.] to the project stakeholders with the overarching goal of ensuring methodological transparency and scalability. These research objects will be made available through a *repository environment* with a supporting metadata system that will facilitate resource discovery and exploitation. Research objects should be accessed through a web-interface with a simple upload and download facility. 

The metadata concerning the research objects will be made available freely (under a [CC0 licence](https://creativecommons.org/choose/zero/)). This will support resource discovery. The research objects themselves will be made available under a licence that constrains their access and re-use. The exact terms of this licence need defining and legal confirmation. Constraint cases include:

1. Only communities who contribute to the repository are allowed to re-use the resources. Repository contribution includes:
	1. Addition of data
	1. Addition of algorithms and models
	1. Co-authorship of papers with a member who is in category 1 and 2^[I appreciate this is somewhat ambigous. How can someone get access at this level without getting access to the data first?]
1. By attribution
	* All research object re-use should include an attribution^[this implies that the metadata should include a citation field for each research object]
1. For research use only (does this mean a *Non-Commercial* clause - and a specific statement about research use)

No stipulation has been made on other types of constraint^[I would argue that these constraining licences should not be used at all]:

* No Derivatives 
* Licensing of Derivatives (for example the [Creative Commons *share-a-like* clause](http://en.wikipedia.org/wiki/Share-alike))
* No Commercial use^[which demands a definition of what commercial use is (and in an academic context as to which academic activities are commercial and which aren't (I would argue that undergraduate teaching is now a commercial activity in the United Kingdom)))]

The initial aim is to build a *Walled garden*  or *closed ecosystem* repository. You get access to the resources by making a contribution which can be used by members. This is seen as a short term catalyst to encourage the sharing of resource objects by the community^[my advice is to make this clear so that once a quantified critical mass has been reached then the whole ecosystem is opened under liberal licences as a platform to encourage extended research, development and collaboration]. A *closed ecosystem* requires some form of federated access in order to function. Access accreditation is therefore a requirement of the repository framework. I

In terms of data it is as yet unclear as to whether this is seen as a data preservation environment^[which will ensure the data is in a format and a facility that ensures access in perpetuity (which formally equates to a [maximum of 25 years](http://archive.icommons.org/articles/preserving-digital-heritage-for-perpetuity-or-at-least-for-the-next-25-years))], a data analysis platform^[which aggregates and materialises the data in a manner which streamlines downstream processing] or both.  This will become clearer when exemplar data is made available^[Darren: could I have some data please :-)]. However, two types of data have been posited:

* Longitudinal
	* Repeatable observations over a small number of subjects
	* State measurements on objects (indoor, outdoor, light, window etc.)
* Transverse
	Questionnaire based
	
Subject to data evaluation and a requirements analysis these data can be fitted into standard data models. It is likely a traditional Object Relational Model for the Longitudinal data and a triplestore for the transverse data. 

The outputs requested by Darren are:

* Sample licence agreement
* 20-30 minute presentation (for the end of March 2015)

This document is a by-product

\newpage

# Assumptions

Assumptions I have made during the preparation of this document

* There are finances in place to pay for an external repository (if necessary) or to fund the development of a project repository if necessary.
* That resource re-users within the *closed ecosystem* will not *leak* the resources into the public domain.
* Contributers will come from different countries and be mainly, but not exclusively, from academic organisations. 

\newpage

# Executive summary and recommendations

TBC

## Repository 

Requires tidying up - 

I would recommend that data from the IEA is held in an independant repository rather than an institutional or bespoke repository. Bespoke repositories (likely to be based on an open source framework) have a high management and cost overhead and will require the hiring of skilled personel to *'reinvent the wheel'*.  Most institutional repositories simply don't yet exist, are immature or cater exclusively on the needs of the host institution (as opposed to a broad consortium from different, or no, institutions). 

There are a number of independant repositories of which a subset allow *closed ecosystems*. Two of the main repositories are:

[**Figshare**](http://figshare.com/)

> Figshare is an online digital repository where researchers can preserve and share their research outputs, including figures, datasets, images, and videos.[1] It is free to upload content and free to access, in adherence to the principle of open data. Figshare is a portfolio company of Digital Science, operated by Macmillan Publishers.

[**Zenodo**](https://zenodo.org/)

> Zenodo is an open dependable home for the long-tail of science, enabling researchers to share and preserve any research outputs in any size, any format and from any science.

My preference would be for Zenodo. Zenodo was funded through [OpenAIRE](https://www.openaire.eu/) in FP7. Zenodo, or a product derived from Zenodo, will become part of the Horizon 2020 environment and as such it is something that the IEA consortium should engage with. It also supports EU wide approaches. Zenodo is free (for deposition and re-use for open and closed data). [Figshare has individual and institutional pricing](http://figshare.com/pricing). This may become complex when sharing data between multiple collaborators.  The modes of accreditation (for example Google, Twitter, ORCID, OpenAIRE^[I would recommend [ORCID](http://orcid.org/0000-0002-2991-811X)]) in Zenodo are broader than FigShare. The Open and Closed community element is also more flexible and is not made unduly complex with a pricing infrastructure. With Horizon 2020 backing it is likely that Zenodo will see greater innovation (for example automated metadata creation is already implemented). Figshare has the benefit of being *at market* for a longer period (more established institutional links) and in accepting larger file uploads (5gb as opposed to 2gb). These upload values are likely to change.

Useful links:

* [Zenodo policies](https://zenodo.org/policies)
* [Zenodo FAQs](https://zenodo.org/faq)
* [Zenodo features](https://zenodo.org/features)
* [Figshare FAQs](http://figshare.com/faqs)
* [Figshare features](http://figshare.com/features)


## Licences

My recommendation is that this community does not need a sample licence. It needs a code of conduct. Ultimately licensing should be mandated by the host research institution or funding body - there can be some latitude in this in terms of licence constraints but the section on licences details the pros and cons. Where no licence is mandated then it is recommended that a CC-BY or ODbL licence is adopted.

See the discussion on licences in the main text.

If Darren agrees I will find some exemplar wording for this. 

## Presentation

If the content of this document adequately details the scenario then it will be whittled down to an image focussed presentation.


\newpage

# Background

*Repositories* are now part of the academic lexicon. In the UK this is a reflection of the stances taken by Research Councils UK (RCUK), the Royal Society, the Engineering and Physical Sciences Research Council (EPSRC) and Horizon 2020. 

> Open inquiry is at the heart of the scientific enterprise. Publication of scientific theories – and of the experimental and observational data on which they are based – permits others to identify errors, to support, reject or refine theories and to reuse data for further understanding and knowledge. Science’s powerful capacity for self-correction comes from this openness to scrutiny and challenge. [@royal_society_science_2012]

The Royal Society’s report *Science as an open enterprise* [-@royal_society_science_2012] identifies how 21^st^ century communication technologies are changing the ways in which scientists conduct, and society engages with, science. The report recognises that ‘open’ enquiry is pivotal for the success of science, both in research and in society. This goes beyond open access to publications (Open Access), to include access to data and other research outputs (Open Data), and the process by which data is turned into knowledge (Open Science).

These concepts are deeply embedded with Horizon 2020. Specific themes are included to provide appropriate capacity [@hudson_open_2012; @_european_2014]: 

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

The vision is to make all outputs of Horizon 2020 openly accessible. Key to this are initiatives like *Zenodo* [@_zenodo_2014]: an FP7 funded repository framework developed by CERN. 

What is happening in academia is part of a broader trend - specifically in terms of *open data*:

>More than 40 countries—from every region of the world and at every stage of development—have established open data initiatives. These nations are opening up all kinds of data sets to promote economic development, spark innovation, and find ways to make government work better. India has released 3,500 data sets, mostly of agricultural information. Singapore has shared 8,600 data sets from 60 public agencies. The World Wide Web Foundation’s Open Data Index rates governments on 14 data-sharing metrics and in 2012 ranked the United States, Mexico, Singapore, the United Kingdom, and New Zealand as the top five most open governments..... The commitment to making data more open was re-affirmed at the June 2013 G8 summit through the Open Data Charter, which establishes “an expectation” that the default policy should be that all government data be published openly. [@mckinsey_open_2013, p. 5]

Open data at a global level is a reality: the Open Knowledge Foundation’s Open Data Index [@open_knowledge_foundation_open_2013], and the Open Data Barometer [@the_web_foundation_the_open_data_institute_open_2013], published by the World Wide Web Foundation, provide an overview on the global state of open data. The global open data movement is as much characterised by the communities of practice surrounding data re-use and engagement as it is by the data itself [@government_digital_service_government_2013].  The recommendations from the Shakespeare review [-@shakespeare_shakespeare_2013] indicate that the amount of government Open Data, at least in the UK, is only going to grow. Reports within the collection 'Beyond Transparency' [@goldstein_beyond_2013] provide an overview of the communities of practice within the public sector. All reports describe the principles of open data: that it should be complete, timely, accessible, able to be processed by a machine, non-discriminatory, available without registration, non-proprietary, and free of any copyright or patent regulations. In addition Coleman refers to the “Three Laws of Open Government Data” [@goldstein_beyond_2013, p. 41]:

* If it can’t be spidered or indexed, it doesn’t exist.
* If it isn’t available in open and machine-readable formats, it can’t engage.
* If a legal framework doesn’t allow it to be repurposed, it doesn’t empower.

Open data has the potential to trigger a revolution in how governments think about providing services to citizens and how they measure their success: this produces societal impact. This will require an understanding of citizen needs, behaviours, and mental models, and  how to use data to improve services.  A McKinsey Global Institute report examines the economic impact of Open Data [@mckinsey_open_2013] and estimates that globally open data could be worth a minimum of $3 trillion annually. This report complements a previous McKinsey report on the impact of Big Data [@mckinsey_company_big_2011]. The expected global increase in demand for open data across all sectors is likely act as a vehicle to remove frictions to data release by governments and bureaucrats. 

From a pragmatic viewpoint the Open and Big data frameworks are still in their early stages and have yet to stabilise and mature. Finding data can be difficult as the quality of the description and discovery metadata is variable. In addition the importance and re-use constraints for data is also poorly documented (data.gov.uk has 16,504 datasets, important data can very easily be swamped). Underlying persistence can also be a problem: in Australia, the government recently pared down its datasets by a third, claiming that some were “junk,” and cleaned up others (e.g., it consolidated 200 files into a single dataset) [@_govt_2013]. Some data isn’t necessarily available in a format that’s easy to use, or in a state where it can be inserted straight into a production environment (it requires validation and enhancement). It is likely that the supporting frameworks will undergo significant changes in the short-term as developers provide feedback (an important component of a hackathon). This builds on Bracken's call for 'an evidence-based assessment of what people want or need' [@goldstein_beyond_2013, p. 273] so that services, frameworks and products can be effectively developed and delivered. 

As an ever larger amount of data is digitized and travels across organizational boundaries, there are a set of policy issues that will become increasingly important, including, but not limited to, privacy, security, intellectual property, and liability. Questions about the intellectual property rights attached to data will have to be answered: Who "owns" a piece of data and what rights come attached with a dataset? What defines "fair use" of data? What are the liability issues when data is re-used outside it's initial scope or use-case [@mckinsey_company_big_2011].

Back to academia. The underlying rationale of Open Data is this: unfettered access to large amounts of ‘raw’ data enables patterns of re-use and knowledge creation that were previously impossible. The creation of a rich, openly accessible corpus of data introduces a range of data-mining and visualisation challenges, which require multi-disciplinary collaboration across domains (within and outside academia) if their potential is to be realised. An important step towards this is creating frameworks which allow data to be effectively accessed and re-used. The prize for succeeding is improved knowledge-led policy and practice that transforms communities, practitioners, science and society.

The need for such frameworks will be most acute in disciplines with large amounts of data, a range of approaches to analysing the data, and broad cross-disciplinary links. Such approaches cannot be undertaken within a single domain of expertise. This vision can only be built by openly collaborating with other scientists and building on shared data, tools and techniques. Open Science advocates opening access to data, and other scientific objects, at a much earlier stage in the research life-cycle than traditional approaches. Open Scientists argue that research synergy and serendipity occur through openly collaborating with other researchers (more eyes/minds looking at the problem). Of great importance is the fact that the scientific process itself is transparent and can be peer reviewed: as a result of exposing data and the processes by which these data are transformed into information, other researchers can replicate and validate the techniques. As a consequence, collaboration is enhanced and the boundaries between public, professional and amateur are blurred. 

The positions taken by Research Councils UK [-@royal_society_science_2012] and the EPSRC [-@epsrc_research_2014] on improving access to data are key catalysts for change. The EPSRC statement is particularly succinct, two of the principles are of particular importance: 

> * Published research papers should include a short statement describing how and on what terms any supporting research data may be accessed.
> * Where access to the data is restricted the published metadata should also give the reason and summarise the conditions which must be satisfied for access to be granted. For example ‘commercially confidential’ data, in which a business organisation has a legitimate interest, might be made available to others subject to a suitable legally enforceable non-disclosure agreement.

This has produced a simple economic issue – if research institutions can not demonstrate that they can manage research data in the manner required by the funding councils then they will become ineligible to receive grant funding from that council. The impact is that the majority of universities are now developing their own, or collaborating on communal, data repositories. Organisations like the Digital Curation Centre (DCC) in the UK are providing leadership and advice to academic organisations [for example @miller_5_2012].

## What is a repository

Formal definition of a repository


## Licensing for a closed community

This project wants to create a *self selecting* group which shares data and other research resources for the common good of the group. The *benefits* of sharing are access to the *cumulative resources* shared by the group. The aim is to increase altruistic data sharing by excluding those members who do not contribute to the community. This strategy is being adopted to incentivise participation. 

However, constraining access to data (which is what a *closed community* entails) has implications on data licensing^[if this data is licensed - see the recommendations] and would entail the creation of a *bespoke licence*. This can have a range of implications which includes incompatibility with requirements from research funders (for example EPSRC and Horizon 2020 as described earlier) and licence incompatibilities when data is mixed with other data with different licence constraints (particularly share-alike constraints^[see discussion below]).

In some respects the problems here may have a lot to do with exposure and re-use of the data at different stages of the research data life-cycle. Most academics see data sharing as a specific stage in the research data lifecycle (for example see Figure \ref{rd_lifecycle}) and that such sharing is part of an archiving and exposure process at the end of a project.

![A view of the Research Data Lifecycle ([provided by Helen Morgan and Nadine Davidson-Wall from the University of Queensland](http://guides.library.uq.edu.au/research-data-management))\label{rd_lifecycle}](http://s3.amazonaws.com/libapps/customers/720/images/Life_Cycle_Diagram.jpg)

This community is likely to be built on different assumptions. It is providing access to the data at an early stage in the research data life-cycle to critical partners and collaborators. Hence, this is less about a single project and more about a community benefit. Data licensing may prove to be a red-herring here. The assumption could be that any data shared within the group will be made available as part of the research data management practices of the collaborators host institutions or funding bodies^[this does beg the question of what happens when there are no such policies in place]. What the community is doing is providing an early access view of this data at an earlier stage of the research data life-cycle. This means that the metadata enrichment activities that facilitate re-use are not only front-loaded but also *actively tested* by an engaged user community. This will allow the community to better document their data resulting ultimately in better discovery. 

### Choosing licences

Licences are fundamental to the successful re-use of content. Licences describe who can use a resource, what they can do with this resource and how they should reference any resource (if at all).

Two lead organisations have developed legal frameworks for content licensing, [Creative Commons (CC)](https://creativecommons.org/) and [Open Data Commons (ODC)](http://opendatacommons.org/). Until the release of [CC version 4](https://wiki.creativecommons.org/4.0), published in November 2013, the CC licence did not cover data. Between them, CC and ODC licences can cover all forms of digital work.

At the top level the licences are permissive public domain licences (CC0 and PDDL respectively) that impose no restrictions on the licensees use of the resource. *‘Anything goes’* in a public domain licence: the licensee can take the resource and adapt it, translate it, transform it, improve upon it (or not!), package it, market it, sell it, etc. Constraints can be added to the top level licence by employing the following clauses:

* BY – By attribution: the licensee must attribute the source.
* SA – Share-alike: if the licensee adapts the resource, they must release the adapted resource under the same licence.
* NC – Non commercial: the licensee must not use the work within a commercial activity without prior approval. Interestingly, in many area of the world, the use of material in university lectures may be considered a commercial activity. The non-commercial restriction about the nature of the activity, not the legal status of the institution doing the work.
* ND – No derivatives: the licensee can not derive new content from the resource.

Each of these clauses decreases the ‘open-ness’ of the resource. In fact, the NC and ND clause are not intrinsically open (they restrict both who can use and what you can do with the resource). These restrictive clauses have the potential to produce license incompatibilities which may introduce profound problems in the medium to long term. This is particularly relevant to the SA clause. Share-alike means that any derived output must be licensed under the same conditions as the source content. If content is combined (or mashed up) – which is essential when one is building up a corpus of resources – then content created under a SA clause can not be combined with content that includes a restrictive clause (BY, NC or ND) that is not in the source licence. This licence incompatibility has a significant impact on the nature of the data commons. It has the potential to fragment the data landscape creating pockets of knowledge which are rarely used in mainstream analysis, research or policy making. This will be further exacerbated when automated data aggregation and analysis systems become the norm^[which are implied as expected in this project]. A permissive licence without clauses like Non-commercial, Share-alike or No-derivatives removes such licence and downstream re-user fragmentation issues.

For completeness, specific licences have been created for Open Government Data. The [UK Government Data Licence for public sector information](http://www.nationalarchives.gov.uk/doc/open-government-licence/version/2/) is essentially an open licence with a BY attribution clause.

It is also worth following the [guidelines of The Open Data Institute](http://theodi.org/guides/publishers-guide-open-data-licensing) and separate out creative content (illustrations, text, etc.) from data content. There is a post advocating [ccZero+ by Dan Cohen](http://www.dancohen.org/2013/11/26/cc0-by/). However, impact tracking may mean that the BY clause becomes a default for academic deposition.

Bepoke licences can be problematic - they tend not to map to national or international licence schemes. This means that they can bring in unintended issues when conflated with other data and, if using automated data aggregation systems, the data might simply be ignored due to licence incompatibilities. For example, the [Archaeology Data Service (ADS)](http://archaeologydataservice.ac.uk/) uses its own [bespoke licence](http://archaeologydataservice.ac.uk/advice/termsOfUseAndAccess) (see Appendix 1). Resources under this licence can only be used for teaching, learning, and research purposes. Of particular concern is their use of the NC clause and possible use of the ND clause (depending on how you interpret the licence). Interestingly, policy changes mean that the use of data under the bespoke ADS licence becomes problematic if university teaching activities are determined to be commercial. It is arguable that the payment of tuition fees represents a commercial activity. If this is true then resources released under the ADS licence can not be used within university teaching which is part of a commercial activity. Hence, the policy change in student tuition and university funding has an impact on the commercial nature of university teaching which has a subsequent impact on what data or resources universities are licensed to use. Whilst it may never have been the intention of the ADS to produce a licence with this potential paradox, it is a problem when bespoke licences are developed, even if they were originally perceived to be relatively permissive licences. In September 2014 the *preamble* to the *terms* of the ADS licence were changed to indicate that commercial useage was acceptable. Unfortunately the *preamble* is not the legal part of the document. There is still ambiguity in the legal part of the document. 


## Concerns about opening up data, and responses which have proved effective

Coleman [@goldstein_beyond_2013] identified that during the early stages of transition within UK government to open data there was fricition. This was split between social cultures within government (secretive and bureaucratic) and 'progressive attempts by governments to exploit the monetization of state data'. Whilst this problem still remains the benefits of open data are becoming apparent to the full stakeholder chain. 

Christopher Gutteridge (University of Southampton) and Alexander Dutton (University of Oxford) have collated a Google doc entitled [‘Concerns about opening up data, and responses which have proved effective‘](https://docs.google.com/document/d/1nDtHpnIDTY_G32EMJniXaOGBufjHCCk4VC9WGOf7jK4/edit#heading=h.2hfedqqfbl6k). This document describes a number of concerns commonly raised by academic colleagues about increasing access to data.

Such friction is an ongoing problem that will be resolved by policy statements from governments and funders (such as those from EPSRC, RCUK and Horizon 2020) and changes in operational norms. 


\newpage

# Outputs

## Sample Licence

My recommendation is that this community does not need a sample licence. It needs a code of conduct. Ultimately licensing should be mandated by the host research institution or funding body - there can be some latitude in this in terms of licence constraints but the section on licences details the pros and cons. Where no licence is mandated then it is redommended that a CC-BY or ODbL licence is adopted.

If Darren agrees I will find some exemplar wording for this. 

## Presentation

If the content of this document adequately details the scenario then it will be whittled down to an image focussed presentation.

