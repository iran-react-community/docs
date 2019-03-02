#Implementing git for Version controlling
Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. version control, also known as revision control or source control. to know more about got version control [read this](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control "About Version Control")

To learn how to work with git effectively, following the "Git Flow" style or different ways depending on the projects.

Branches are a way to isolate different paths of development, which can then be combined (aka “merged”) into a single branch (often named “master”). Refer to [this short guide](https://help.github.com/en/articles/create-a-repo).


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

#summary 
Git allows a wide variety of branching strategies and workflows. Because of this, many organizations end up with workflows that are too complicated, not clearly defined, or not integrated with issue tracking systems. Therefore, we propose combination of [feature-driven](https://en.wikipedia.org/wiki/Feature-driven_development "Feature-driven development (FDD) is an iterative and incremental software development process. It is a lightweight or Agile method for developing software.") development and [feature branches](https://martinfowler.com/bliki/FeatureBranch.html "The basic idea of a feature branch is that when you start work on a feature you take a branch of the repository to work on that feature. ") with issue tracking.


