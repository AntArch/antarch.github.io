Date: 2014-01-06 16:00
Title: Setting up a python environment in Arch Linux - basics
Category: Python, Arch
Tags: Python, Arch, Set-up, virtual environment
#Aims:
Set up a python environment where I can run multiple self contained versions of python under virtualenv.

#URLs used:
* <http://docs.python-guide.org/en/latest/dev/virtualenvs/>
* <http://dabapps.com/blog/introduction-to-pip-and-virtualenv-python/>
* <http://virtualenvwrapper.readthedocs.org/en/latest/>

#TL;DR
* Do use pip
* Don't use easy-install (apart from to install pip)
* Do install virtualenv
* Don't use virtualenv to manage virtual environments
* Do install virtualenvwrapper
* Do use virtualenvwrapper to manage virtual environments

#SetUpCode:
    sudo pip install virtualenv   
    sudo pip install virtualenvwrapper
	sudo geany .bashrc
	<addTheFollowingToBashrc>
		# set the workonhome and virtualenvwrapper_python
		export WORKON_HOME=$HOME/.virtualenvs
		export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3.4
		source /usr/bin/virtualenvwrapper.sh
	</addTheFollowingToBashrc>

#Useage:

	mkvirtualenv <virtualenvironment name> #create a virtual environment using default settings
	mkvirtualenv -p /usr/bin/python3.4 <virtualenvironment name> #create a virtual environment using python3.4
	mkvirtualenv -p /usr/bin/python2.7 <virtualenvironment name> #create a virtual environment using python2.7
	lsvirtualenv #List the virtual enviornments: 
	workon <virtualenvironment name> #Use a specific virtual environment
	rmvirtualenv <virtualenvironment name> #Remove a specific virtual environment
	deactivate #stop using the current virtual environment

#Why:
By forcing your code to work against self-contained python environments stored in unique 'virtual environments' you insulate yourself from changes in the underlying libraries which may break your code. 

#What does virtualenv do:
virtualenv solves this problem by creating a completely isolated virtual environment for each of your programs. An environment is simply a directory that contains a complete copy of everything needed to run a Python program, including a copy of the python binary itself, a copy of the entire Python standard library, a copy of the pip installer, and (crucially) a copy of the site-packages directory mentioned above. When you install a package from PyPI using the copy of pip that's created by the virtualenv tool, it will install the package into the site-packages directory inside the virtualenv directory. You can then use it in your program just as before.

#What does virtualenvwrapper do:
* Organizes all of your virtual environments in one place.
* Wrappers for managing your virtual environments (create, delete, copy).
* Use a single command to switch between environments.
* Tab completion for commands that take a virtual environment as argument.
* User-configurable hooks for all operations (see Per-User Customization).
* Plugin system for more creating sharable extensions (see Extending Virtualenvwrapper).

