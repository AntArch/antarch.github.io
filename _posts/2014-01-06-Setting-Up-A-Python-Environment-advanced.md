---
Date: 2014-01-06 18:00
Title: Setting up a python environment in Arch Linux - advanced
Category: Python, Arch
Tags: Python, Arch, Set-up, virtual environment
layout: post
---

#Aims:
The python environments then need populating with libraries etc. This is the place to get some standard setups

#URLs used:
* <http://www.thisisthegreenroom.com/2011/installing-python-numpy-scipy-matplotlib-and-ipython-on-lion/>

#TL;DR
* use conventions and regular naming for your virtual environments
	* prefixes
		* p2_ for python2
		* p3_ for python3

#Useful things:
List the virtual environments

	lsvirtualenv

Work within a specific virtual environment

	workon <virtualenvironment name> #Use a specific virtual environment

Stop using a specific virtual environment

	deactivate #stop using the current virtual environment

List what version of python and which libraries are installed

	python -V
	help('modules')
	pip freeze
	#for all currently used modules (useful if looking to re-build a bespoke environment)
	import sys as s
	print s.modules.keys()

#Installing python library schemes
	workon <virtualenvironment name> #see list using lsvirtualenv
	pip install <library name> #copy and paste library schemes from below
	deactivate

I recently moved back to ubuntu (or mint at least) and not everything installed properly. Foe GDAL the following helped:

	export CPLUS_INCLUDE_PATH=/usr/include/gdal
	export C_INCLUDE_PATH=/usr/include/gdal


	
#Python library schemes
These workin both Python 2 and 3. Specific python 2 dependencies are noted.

##For Python2 always include
	pip install future

Amongst other things this provides consitency with the print statement for python3 using:

	from __future__ import print_function
	
##Pre-requisites

You'll need a fortran compiler for scipy

	sudo pacman -S gcc-fortan

##Data Science
	pip install numpy
	pip install scipy
	pip install pandas
	pip install matplotlib
	pip install tornado
	pip install pyzmq
	pip install ipython[all]
	
Firing up ipython-notebook

	ipython notebook --pylab=inline #remember to check the port number if, like me, you automatically start up a default ipython-notebook instance
##Stats
	pip install patsy
	pip install statsmodels # [not working in python3](http://stackoverflow.com/questions/23343484/python-3-statsmodels)
	pip install sympy


##Semantic Web
	pip install rdflib
	pip install SPARQLWrapper
	pip install FuXi #not working - google this
	
##Code improvement
	pip install pyflakes
	pip install pylint
	pip install rope
	
##Connecting to datasources
	pip install psycopg2 #postgres
	pip install urllib3 #import data from URLs

##Generically useful libraries
	pip install datetime
	pip install simplejson
	pip install zipfile # not installing in python 2 or 3
	
##Geo
	pip install folium
	pip install gdal
   	pip install pyproj #projection and reprojection library
    	pip install basemap  # not installing in python 2 or 3 try: [compiling by hand](https://github.com/matplotlib/basemap)
    	pip install pyshp
    	pip install geojson
	pip install pyproj basemap gdal shapely fiona
	pip install Descartes geoJSON psycopg2 SQLAlchemy
	[Cartopy needs compiling](https://github.com/SciTools/cartopy)
    
##Computer vision
	pip install pil # not installing in python 2 or 3 TRY: pip install --allow-external pil --allow-unverified pil pil

	
##Visualisation
This is mainly to play about with bokeh. The dependencies for this are, unfortunately, mixed.

Had trouble installing bokeh. Bottom this out later

###Dependencies
	pip install flask Redis Requests gevent gevent-websocket
   	pip install bokeh

##DataFormats

	pip install netCDF4
	pip install pyyaml

#Datbase querying

	pip install sqlalchemy


	

