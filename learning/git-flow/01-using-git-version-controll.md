##Intro
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



refs:
https://docs.gitlab.com/ee/workflow/gitlab_flow.html