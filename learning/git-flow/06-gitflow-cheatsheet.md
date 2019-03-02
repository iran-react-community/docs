#Intro
This is a quick reference on git-flow, if you needed more detail a descriptive example and a quick presentation provided on the following links.

1. Step-by-Step Guide to the Git and Release Management with gitflow documented [here](https://rubygarage.org/blog/git-and-release-management-workflow "use a task management system (Jira) for managing software product development workflow in compliance with the agile software development methodology.")

1. And there is a presentation explaining gitflow : [git-flow presentation](http://rubygarage.github.io/slides/git/gitflow#/ "Gitflow is a set of scripts that extend git (Can use standard git commands but scripts make it easier)")

#Git-flow Cheat Sheet
Initialize a new repository inside an existing git repository with 
`git flow init.`
##Types of branches
- Feature branch
	- For developing new features
- Release branch
	- Staging area for new releases
- Hotfix branch
	- Production fixes (based on master)
- Bugfix branch
	- Develo­pment fixes (based on develop)
- Support branch
	- Production fixes for a specific release

###Features
- Show feature branches
	- `git flow feature [list]`
- Start a new feature
	- `git flow feature start FEATUR­ENAME`
- Publish feature branch to remote
	- `git flow feature publish FEATUR­ENAME`
- Finish up a feature
	- `git flow feature finish FEATUR­ENAME`
> Finishing a feature branch will merge it into develop.

###Releases
- Show release branches
	- `git flow hotfix [list]`
- Start a new release
	- `git flow hotfix start VERSION`
- Publish release branch to remote
	- `git flow hotfix publish VERSION`
- Finish up a release
	- `git flow hotfix finish VERSION`
> Finishing a release branch will merge it into master and develop while also tagging it.

###Hotfixes
- Show hotfix branches
	- `git flow hotfix [list]`
- Start a new hotfix
	- `git flow hotfix start FIXNAME`
- Publish hotfix branch to remote
	- `git flow hotfix publish FIXNAME`
- Finish up a hotfix
	- `git flow hotfix finish FIXNAME`
> Finishing a hotfix branch will merge it into master.

###BugfixesShow 
- bugfix branches
	- `git flow bugfix [list]`
- Start a new bugfix
	- `git flow bugfix start FIXNAME`
- Publish bugfix branch to remote
	- `git flow bugfix publish FIXNAME`
- Finish up a bugfix
	- `git flow bugfix finish FIXNAME`
> Finishing a bugfix branch will merge it into develop.



###Support
- Show support branches
	- `git flow support [list]`
- Start a new support branch
	- `git flow support start VERSION`


