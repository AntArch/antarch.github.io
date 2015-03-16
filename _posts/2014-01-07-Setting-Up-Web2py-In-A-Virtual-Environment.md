Date: 2014-01-07 17:00
Title: Setting up a web2py in a virtual environment Arch Linux
Category: Python, Arch
Tags: Python, Arch, Set-up, virtual environment, web2py
#Aims:
Setting up a web2py in a virtual environment Arch Linux

#URLs used:
* <http://www.web2pyslices.com/slice/show/1464/setting-up-web2py-in-a-virtual-environment>

#TL;DR
* pre-requisites
	* install mercurial
		* so do this in python 2.7
	* A cloned virtual env
* Navigate into your virtual environment
	* clone web2py using mercurial
	* start web2py

#Code

##pre-requisites
	cpvirtualenv p2_generic p2_rsr
	workon p2_rsr
	pip install mercurial
	
##implementation
	workon p2_rsr
	cd .virtualenvs/p2_rsr #move to virtualenv directory
	hg clone https://code.google.com/p/web2py/ web2py #clone web2py in this directory
	./bin/python ./web2py/web2py.py #launch web2py
	

