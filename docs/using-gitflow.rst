===================
How to use Git Flow
===================


:Author:    Jan Börner
:Date:      2012-09-06



Abstract
========

In the following tutorial, i want to show you how you can use git flow......
I will use a example project, which shows the commands of git flow and what
it is able to do. Moreover you should get a felling for it..... have fun ;) 

What is git flow?
================

Git flow is a command line tool, which support the programmer to use a certain 
git workflow. What is meaning by "certain workflow"? In this documentation http://nvie.com/posts/a-successful-git-branching-model/ 
you find all information you need. Git flow is nothing more like a way to write less and do more with git...... 
To install git flow, follow the steps in this documentation https://github.com/nvie/gitflow/wiki/Installation


Let's go
========

First of all we have to create and initialize a git repo  ..... :: 
	

	$ mkdir nexiles.git.flow
	$ git init
	$ git flow init
		
	
Now git flow will ask you some questions....


It ask you which branch you want for product release ::


	 Branch name for production releases: [master]

Git flow gives you always a default name for branch, in this case "master"


Next, you are asked which branch you want for develop::


	 Branch name for "next release" development: [develop]


Git flow gives you the default "develop"
just press enter....

Next, git flow want's to know how feature-branches should start:: 


	How to name your supporting branch prefixes?
	Feature branches? [feature/]


You get "feature/" as default, enter this.


As next, git flow also want's to know this for release, hotfix and support branches.... ::


	Release branches? [release/]
	Hotfix branches? [hotfix/]
	Support branches? [support/]


Enter this......


Hold on!

Git flow ask you if you want a version tag prefix 
So what is this?
You can give a project a tag name, so every release gets this as default name...
For E.X we take as tag "day-of-releas" and give to every release the current date as branch name, we get
automaticly the tag "day-of-release-06112012".
For our project we take "nx-release" :: 


	Version tag prefix? [] nx-release


Cool stuff...... you're done ;) let's start with our project...... 


Starting to use Git flow 
=========================


Feature Branches
----------------


To see how git flow works, we create a little project...... 
A customer want a hello world html page from us... no problem, we do this.
So first of all we need a feature branch for our html code. Type ::

	$ git flow feature

No we get the information that currently no feature branch exists ::

	No feature branches exist.
	You can start a new feature branch:
	git flow feature start <name> [<base>]

So let's create one. Type :: 


	$ git flow feature start "html-code"
	
	
so make shure that you are be in the feature
branch and creat a index.html ... copie the following code ::



	<html>
		<head>
		<body>
		<h1>Hello World</h1>
		</body>
	</html>



Ok.... add and commit your changes, than type::



	$ git flow feature finish html-code



Git flow merge the feature-branch into develop an close it.
Moreover git flow add's your commits in the feature-branche to develop...



Release Branches
----------------


So.... now we want to make the first release..... no problem, type::



	$ git flow release


No we get the information that we have currently no  releases.... So let's create one.
To do this just type:: 



	$ git flow release start 1.0
	
 

No we have created a new releas.Up now we can't add anything to this releas... It's fix!
The only thing we do on release branches is fixing bugs!
We do this to prepare a forthcoming release...
So what is git doing? Lets have a look on the output.. type::


	$ git flow release finish '1.0'

You will get the output::

	Switched to branch 'master'
	Merge made by the 'recursive' strategy.
	docs/.introduction.rst.swp  |  Bin 0 -> 12288 bytes
	docs/.using-gitflow.rst.swo |  Bin 0 -> 12288 bytes
	docs/.using-gitflow.rst.swp |  Bin 0 -> 12288 bytes
	docs/git-workflow.png       |  Bin 0 -> 145643 bytes
	docs/introduction.rst       |   48 ++++++++++++++++++++++++++++++++++
	docs/using-gitflow.rst      |   96 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	src/index.html              |    7 +++++
	7 files changed, 151 insertions(+)
	create mode 100644 docs/.introduction.rst.swp
	create mode 100644 docs/.using-gitflow.rst.swo
	create mode 100644 docs/.using-gitflow.rst.swp
	create mode 100644 docs/git-workflow.png
	create mode 100644 docs/introduction.rst
	create mode 100644 docs/using-gitflow.rst
	create mode 100644 src/index.html
	Deleted branch release/1.0 (was d4bd16a).

	Summary of actions:
	- Latest objects have been fetched from 'origin'
	- Release branch has been merged into 'master'
	- The release was tagged 'nx-releas1.0'
	- Release branch has been back-merged into 'develop'
	- Release branch 'release/1.0' has been deleted


If you look at the summary of actions, you can see what git do...... 
Now we have our releas 1.0 on master. 
Cool ;) 



Sooo... beacuse we're so diligently developer we want to add a cool js function to our next release, so you just 
have to do the same like before. Make a new branch and add a js hello world function to index.html and finisch the feature-branch
afterwards. So now we've a new feature in our develop branch. 



Hotfix Branches 
---------------


Now we have a problem! The customer calls us and say that his version of the hello world site is brick!
We forgot to close the head tag and now the site is just empty..... damn! 



So what now?
We have to make a hotfix! 
Make a branch on which we can solve this problem.


type::

	$ git flow hotfix start "head-bug"


Git flow creates a branch named "hotfix/head-bug".
Open the file and fix this, afterwards type:: 




	$ git flow hotfix finish head-bug



So what happend?
Git flow merged head-bug to master and develop, and deleted head-bug afterwards.

Cool Stuff......
 

Make a Bugfix on a Release Branch
---------------------------------


OK, what we learned out of this? We should make a bugfix before we throw the release on master next time......
But the customer is a nice guy and he is not resent.... He want to have a style feature which should show his
hello world headline red and he also is intresting in our javascript stuff... great ;)

Let's make new feature branch for the css stuff..... Now you know how you have to do this ;) 
Add this to your index.html::


	<style type="text/css" >


		h1 {color:red;



	</style>


finish the feature and make a new release. 
This time we look very carefull if we made mistakes. And.... ohhhh.... Yes we did ;)
We have forgotten to close the style instruction for our headline! Fix this before you can finish the release.....



Support Branches
----------------



What is a support branch? 
The idea of a support branch is, that you still can support older versions
of software products. This is generally for some big lazy client that don’t want to upgrade for some obscure reason...... 
This branch will be created, but as far as I know it won’t ever be deleted and will simply become a new sub-version of a current 
hotfix or major release. Moreover i have to note, that this is still a very experimental feature of Gitflow, so you should use it with caution.



Our hello world page is now in version 1.5 and we have a amount of customers.... 

Great ;)

But one customer from the beginning didn't want to upgrade since version 1.0 .... so what should we do? We created a support branch
just for him, because we're so friendliy ;) 

 
we did it like this::


	$ git flow support start Support_V_1.0 nx-releas1.0


Keep the syntax in mind ::

	git flow support start [supportName] [tagName]


Now we have a support version for 1.0 and the customer is happy ;) 



Conclution 
==========

So..... we're done.....

 
I hope you got a impression, the understanding and the basic skills which you need
to use git flow and this kind of workflow.....
At the end of these tutorial you will find some sources about this topic.....
For notes, supplements or improvments write at jan.boerner@nexiles.com.


Bye bye.......



Sources
=======

- http://yakiloo.com/getting-started-git-flow/
- http://splitshade.wordpress.com/2012/04/22/git-flow-einfaches-arbeiten-mit-dem-perfekten-git-workflow/ 
- http://nvie.com/posts/a-successful-git-branching-model/
- https://github.com/nvie/gitflow


