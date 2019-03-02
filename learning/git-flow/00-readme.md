##Documenting Software Development using GitFlow
There are following six phases in every Software development life cycle model:

- Requirement gathering and analysis
- Design
- Implementation or coding
- Testing
- Deployment
- Maintenance

Having more than just source code in a repository is a very good thing, Documentation also should have a full history and the ability to revert to an earlier versison if that becomes necessary. A version control system is perfect for this.


1. It groups all of your resources together and turns the project into a cohesive, centralized entity rather than a scattered collection of files. Contributors/employees know where to find everything, rather than sending "Where do I change the documentation for feature x?" emails.

1. You'll want to keep things organized. Have a system for separating the src from the images from the docs. You can always add a .gitignore to a directory to keep the repository and history clean. Because Git commits are file-based,* you can decouple source changes from documentation changes as strongly as you like.

1. Git is great for documentation versioning as long as it's text-based.

1. documentation should be versioned right alongside the code.


#What is version control
Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. version control, also known as revision control or source control. to know more about git version control [read this](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control "About Version Control")
and for knowing Benefits of version control use this article:

[What is version control](https://www.atlassian.com/git/tutorials/what-is-version-control "Version control systems are a category of software tools that help a software team manage changes to source code over time. Version control software keeps track of every modification to the code in a special kind of database. If a mistake is made, developers can turn back the clock and compare earlier versions of the code to help fix the mistake while minimizing disruption to all team members.")

##Git basics
Git is a free and open source version control system, originally created by Linus Torvalds in 2005. Unlike older centralized version control systems such as SVN and CVS, Git is distributed: every developer has the full history of their code repository locally. This makes the initial clone of the repository slower, but subsequent operations such as commit, blame, diff, merge, and log dramatically faster.

Git also has excellent support for branching, merging, and rewriting repository history, which has lead to many innovative and powerful workflows and tools. Pull requests are one such popular tool that allow teams to collaborate on Git branches and efficiently review each others code. Git is the most widely used version control system in the world today and is considered the modern standard for software development.

##How Git works
Here is a basic overview of how Git works:

1. Create a "repository" (project) with a git hosting tool (like Bitbucket)
1. Copy (or clone) the repository to your local machine
1. Add a file to your local repo and "commit" (save) the changes
1. "Push" your changes to your master branch
1. Make a change to your file with a git hosting tool and commit
1. "Pull" the changes to your local machine
1. Create a "branch" (version), make a change, commit the change
1. Open a "pull request" (propose changes to the master branch)
1. "Merge" your branch to the master branch

#Implementing git for Version controlling
One of the biggest advantages of Git is its branching capabilities. Unlike centralized version control systems, Git branches are cheap and easy to merge. This facilitates the feature branch workflow popular with many Git users.

Branches are a way to isolate different paths of development, which can then be combined (aka “merged”) into a single branch (often named “master”). 
![eature branches provide an isolated environment for every change to your codebase.](https://wac-cdn.atlassian.com/dam/jcr:fcad863b-e0da-4a55-92ee-7caf4988e34e/02.svg?cdnVersion=lb)

[**Why Git for your organization**](https://www.atlassian.com/git/tutorials/why-git "Switching from a centralized version control system to Git changes the way your development team creates software. And, if you’re a company that relies on its software for mission-critical applications, altering your development workflow impacts your entire business.")

> Before getting into the different branching styles, it's important to remember that, although many git clients treat slashes ("/") as a directory separator, there is no such thing as folders or directories in the git specification. 

#Gitflow
Basically, a GitFlow organization would have these three folders:

- feature[s]
- hotfix[es]/fixes
- release[s]

![](https://res.cloudinary.com/practicaldev/image/fetch/s--zSTlxO3C--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://raw.githubusercontent.com/kblok/kblok.github.io/master/img/git-branches/gitflow.png)

with adding two more folders to our Gitflow repos, depends on project needs, we can make it more agile:

- Docs: For branches related to markdown or release documents.
- Task: For branches which are neither features nor fixes. Such as, clean up scripts or refactors.


#Styles
Revision control manages changes to a set of data over time. These changes can be structured in various ways:
###BPMP (Branch-Push-Merge-Prune)
I’ve seen this a lot in many projects. The branch-push-merge-prune is the anti-folder method. I'm not saying that chaos is a way of organizing branches. People using this method like to have their working copy clean. They would just branch, push, create a pull request and then delete the branch (manually or via git fetch prune) as soon as the PR is merged.

###Module-based
I found myself using what I call a "module-based" branching model on a big project where I got quite lost in a sea of features and fixes. So I started to create branches based on its modules.

![](https://res.cloudinary.com/practicaldev/image/fetch/s--GvozHRtc--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://raw.githubusercontent.com/kblok/kblok.github.io/master/img/git-branches/module-based.png)

> You could mix Gitflow with this module-based approach, something like "backoffice/billing/fixes/billing-values", but that may be too much.

###Version-based
I first saw Meir using this approach and I loved it. It’s great for projects like Puppeteer-sharp where the roadmap is clear.
In a version-based repo you create each branch inside a "vX.X" folder. What is cool about this is that it’s time-based, so it's easier to find branches and also it's super easy to delete old versions with this simple git command:

    git branch | grep -e "vX.X/" | xargs git branch -D

![](https://res.cloudinary.com/practicaldev/image/fetch/s--1EvoAWh1--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://raw.githubusercontent.com/kblok/kblok.github.io/master/img/git-branches/version-based.png)

Again, this could be mixed with Gitflow folders, but...

###Ticket-based
If tickets numbers (tickets, issues or whatever you call them) are part of your team's language using a ticket-based system could be a perfect fit.
You could use a folder, such as "tickets/242" or "issues/242", or just simply call it "242".
![](https://res.cloudinary.com/practicaldev/image/fetch/s--iephL5do--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://raw.githubusercontent.com/kblok/kblok.github.io/master/img/git-branches/tickets-based.png)

> note: 
> Git allows a wide variety of branching strategies and workflows. Because of this, many organizations end up with workflows that are too complicated, not clearly defined, or not integrated with issue tracking systems. Therefore, we propose combination of [feature-driven](https://en.wikipedia.org/wiki/Feature-driven_development "Feature-driven development (FDD) is an iterative and incremental software development process. It is a lightweight or Agile method for developing software.") development and [feature branches](https://martinfowler.com/bliki/FeatureBranch.html "The basic idea of a feature branch is that when you start work on a feature you take a branch of the repository to work on that feature. ") with issue tracking.


##Using gitflow style
Organizations coming to Git from other version control systems frequently find it hard to develop a productive workflow. To use git efficiently we're integrates the Git branch-and-merge workflow with an issue tracking system. It offers a simple, transparent, and effective way to work with Git.

When converting to Git, you have to get used to the fact that it takes three steps to share a commit with colleagues. Most version control systems have only one step: committing from the working copy to a shared server. In Git, you add files from the working copy to the staging area. After that, you commit them to your local repo. The third step is pushing to a shared remote repository. After getting used to these three steps, the next challenge is the branching model.

###What a Branch Is
When you commit in Git, Git stores a commit object that contains a pointer to the snapshot of the content you staged, the author and message metadata, and zero or more pointers to the commit or commits that were the direct parents of this commit: zero parents for the first commit, one parent for a normal commit, and multiple parents for a commit that results from a merge of two or more branches.

> A [branch](https://git-scm.com/book/en/v1/Git-Branching-What-a-Branch-Is "a branch in Git is in actuality a simple file that contains the 40 character SHA-1 checksum of the commit it points to") in Git is simply a lightweight movable pointer to one of these commits. The default branch name in Git is master. As you initially make commits, you're given a master branch that points to the last commit you made. ... It keeps a special pointer called HEAD.

###Using branch-based deploys in your continuous delivery pipeline
We often use terms like "pipeline" to describe the continuous flow of code from your repo to your users.

branch-and-merge workflow lets you tackle thorny bugs, try out new technologies, or just start coding a new feature from scratch without the risk that your changes will prevent your teammates from forging ahead with their own tasks.

#The only rule!
Anything in the **master** branch is deployable. Other than this, code in the master branch is always in a deployable state; when you fix or add something new in a branch and then you merge it onto the master , you don't deploy automatically, but you can assume you changes will be up and running in a matter of hours.


#Using git-flow for documenting projects


[Git-Flow CheatSheet](https://danielkummer.github.io/git-flow-cheatsheet/index.fa_FA.html)

[Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)

###Tools to impliment gitflow 
[https://www.sourcetreeapp.com/](https://www.sourcetreeapp.com/ "Sourcetree simplifies how you interact with your Git repositories so you can focus on coding. Visualize and manage your repositories through Sourcetree's simple Git GUI.")


To start with git use [this tutorial](https://help.github.com/en/articles/create-a-repo).



