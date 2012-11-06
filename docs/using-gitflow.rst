===================
How to use Git Flow
===================


:Author:    Jan Börner
:Date:      2012-09-06



Abstract
========

In the following tutorial i want to show you how you can use git flow......
I will use a example project, which shows the commands of git flow and what
it is able to do.

Wtf is git flow?
================

Git flow is a command line tool, which support the programmer to use a certain 
git workflow. What is meaning by "certain workflow"? In this documentation http://nvie.com/posts/a-successful-git-branching-model/ 
you find all information you need. Git flow is nothing more like a way to write less and make more with git...... 
To install git-flow, follow the steps in this documentation https://github.com/nvie/gitflow/wiki/Installation


Getting started
===============

First of all we have to create and initialize a git repo  ..... ::
	

	$ mkdir git-flow-repo
	$ git init
	$ git flow init
		
	
Now git-flow will ask you some questions....


First of all it ask you which branch you want for product release ::


	 Branch name for production releases: [master]

Git flow gives you always a default name for branch, in this case "master"


Next, you are asked which branch you want for develop::


	 Branch name for "next release" development: [develop]


Git flow gives you the deafault "develop"
Just enter....

Next, git flow want's to know how feature-branches should start:: 


	How to name your supporting branch prefixes?
	Feature branches? [feature/]


You get "feature/" as default, enter this.


As next git-flow also want's to know this for releas, hotfix and support branches.... ::


	Release branches? [release/]
	Hotfix branches? [hotfix/]
	Support branches? [support/]


Enter this......

Git also ask you if you want a version tag prefix ::

	
	Version tag prefix? []


So what is this?
You can give a project somthing like a "stamp" so every releas gets this as default name...
For E.X we take as tag "day-of-releas" and give to every releas the current date we get
automaticly the stamp "day-of-relase-06112012".









