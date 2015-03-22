---
Date: 2014-01-07 17:10
Title: Setting up rsr under web2py in a virtual environment Arch Linux
Category: Python, Arch, web2py
Tags: Python, Arch, Set-up, virtual environment, web2py
layout: post
---

#Aims:
Setting up rsr under web2py in a virtual environment under Arch Linux
Install flot.js

#URLs used:
* <https://github.com/dontgitit/rm>
also look at
* <https://github.com/dontgitit/bph>

#TL;DR
* Log into your virtual environment
* fire up web2py
	* enter admin interface
		* create new project
			* type in 'application name': rsr_app
		* click 'create'
		


#Code

	workon p2_rsr
	cd .virtualenvs/p2_rsr #move to virtualenv directory
	./bin/python ./web2py/web2py.py #launch web2py
	

