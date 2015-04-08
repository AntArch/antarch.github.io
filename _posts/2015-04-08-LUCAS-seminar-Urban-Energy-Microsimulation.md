---
Date: 2015-04-08 10:47
title:  'LUCAS seminar Urban Energy Microsimulation'
author: Anthony Beck for Darren Robinson
layout: post
Category: LUCAS, seminar
Tags:  LUCAS, seminar
bibliography: references.bib
csl: harvard.csl
abstract: |
  
  
  \newpage
---

LUCAS seminar Urban Energy Microsimulation - Presentation by Darren Robinson

[Flash version is online](http://antarch.github.io/mindmaps/LUCAS_Seminar_series.html)

Text version is below.

Background

# LUCAS_Seminar_Series 20150408

* Urban Energy Microsimulation
	* Darren Robinson
2002+
	* SUNTool
		* Sustainable Urban Neighbourhood modelling tool
		* Segmentation between interior and exterior of building
			* Based solely on the DEM?
		* Essentially Solar Insolation modelling
		* Vector model
	* DEM based approach
* CitySim <http://citysim.epfl.ch/>
	* Successor to SUNTool
	* Overview
		* Summary
			* Detailed decision support tool
				* For sustainable planning
			* Micro-simulation
			* Based on modelling
				* urbane energy
				* matter flows
			* Accounts for
				* Occupants behavious
				* Urban (radiative) climate
				* Synergetic energy and matter exchanges
			* Seen as
				* Productive
					*  Multi Scales
				* Intuitive
		* Workflow
			* Create/import 3d model (or clones)
				* Formats
					*  DXF
				* Parent child inheritance
					*  Called clones
					*  Each 'clone' type shares the same attributes
			* Describe envelope composition
			* Describe occupanys and appliance scheudiles
			* + more
		* Solver
			* 3D scene
				* In XML
			* Radiative model pre-process
				* From
					*  Sun
					*  Sky
					*  Reflective
			* Radiation model
			* Thermal model
				* feedback to
					*  Radiation model
						*  via
							*  Behavioural model
				 				* Open
				 					*  Blind
				 					*  Windows
				 				* Turn on/off heating
			* HVAC models <https://en.wikipedia.org/wiki/HVAC>
				* heating, ventilation, and air conditioning
				* feedback to 
					*  Thermal model
			* ECS models
				* feedback to 
					*  HVAC models <https://en.wikipedia.org/wiki/HVAC>
		* Radiation exchange
			* Calculate sky radiance distribution for a discretized sky vault
			* Previous approach
				* Isotropic
				* others
		* Calculate occlusion
			* Ends up aggregating the occluding surfaces into a single element
			* Becomes
				* Visible sky
				* Occluded area
		* Calculate radiance
			* Add contribution from
				* Sky
				* Sun
				* Reflected
			* Assumes LAMBERTIAN reflectance characteristics <https://en.wikipedia.org/wiki/Lambertian_reflectance>
			* Reflectance
				* Some others may well be SPECULAR <https://en.wikipedia.org/wiki/Specular_reflection>
				* Models of reflecatnce <https://commons.wikimedia.org/wiki/File:Reflection_models.svg>
					*  Note this smooth and roghness of surface is wavelength dependent
		* Solve the equation
			* Shortwave radiation
			* Longwave radiation
	* Other bits
		* HVAC moelling
		* Energy conversion systems
			* Solar
			* Wind
			* PVAC
	* Comparators
		* ESP-r <http://www.esru.strath.ac.uk/Programs/ESP-r.htm>
		* radiance <https://en.wikipedia.org/wiki/Radiance_(software)>
	* Stochastic simulation <https://en.wikipedia.org/wiki/Stochastic>
		* Physical systems in which we are uncertain about the values of parameters, measurements, expected input and disturbances are termed Stochastic Systems.
		* The same occupant may respond differently on different occassions
		* We may encounter considerable difference to difference individuals under identical scenamrios
		* Methods
			* Bernoulli process <https://en.wikipedia.org/wiki/Bernoulli_process>
				* Probability
			* Markov Chain <https://en.wikipedia.org/wiki/Markov_chain>
				* Transitions
			* Continuous time random process
				* Survival analysis <https://en.wikipedia.org/wiki/Survival_analysis>
		* Applying
			* Forward selection
				* tends to be linear regression
			* Cluster analysis
			* k-fold cross validation <https://en.wikipedia.org/wiki/Cross-validation_(statistics)#k-fold_cross-validation>
* No-MASS
	* Nottingham Multi-Agent Stochastic Simulation
* New opportunities
	* Secondment to UC berkeley
		* UrbanSim <http://www.urbansim.org/Main/WebHome>
		* Co-Simulation
* Things to do
	* ARB - consider presentation on CityGML
	
