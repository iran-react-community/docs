##Creating a release branch

Release branches are created from the develop branch. For example, say version 1.1.5 is the current production release and we have a big release coming up. The state of develop is ready for the “next release” and we have decided that this will become version 1.2 (rather than 1.1.6 or 2.0). So we branch off and give the release branch a name reflecting the new version number:
<div class="codehilite"><pre><span class="gp">$</span> git checkout -b release-1.2 develop
<span class="go">Switched to a new branch "release-1.2"</span>
<span class="gp">$</span> ./bump-version.sh 1.2
<span class="go">Files modified successfully, version bumped to 1.2.</span>
<span class="gp">$</span> git commit -a -m <span class="s2">"Bumped version number to 1.2"</span>
<span class="go">[release-1.2 74d9424] Bumped version number to 1.2</span>
<span class="go">1 files changed, 1 insertions(+), 1 deletions(-)</span>
</pre></div> 

After creating a new branch and switching to it, we bump the version number. Here, bump-version.sh is a fictional shell script that changes some files in the working copy to reflect the new version. (This can of course be a manual change—the point being that some files change.) Then, the bumped version number is committed.

This new branch may exist there for a while, until the release may be rolled out definitely. During that time, bug fixes may be applied in this branch (rather than on the develop branch). Adding large new features here is strictly prohibited. They must be merged into develop, and therefore, wait for the next big release.

##Finishing a release branch 
When the state of the release branch is ready to become a real release, some actions need to be carried out. First, the release branch is merged into master (since every commit on master is a new release by definition, remember). Next, that commit on master must be tagged for easy future reference to this historical version. Finally, the changes made on the release branch need to be merged back into develop, so that future releases also contain these bug fixes.

The first two steps in Git:
<div class="codehilite"><pre><span class="gp">$</span> git checkout master
<span class="go">Switched to branch 'master'</span>
<span class="gp">$</span> git merge --no-ff release-1.2
<span class="go">Merge made by recursive.</span>
<span class="go">(Summary of changes)</span>
<span class="gp">$</span> git tag -a 1.2
</pre></div>

The release is now done, and tagged for future reference.	

> You might as well want to use the -s or -u <key> flags to sign your tag cryptographically.

To keep the changes made in the release branch, we need to merge those back into develop, though. In Git:
<div class="codehilite"><pre><span class="gp">$</span> git checkout develop
<span class="go">Switched to branch 'develop'</span>
<span class="gp">$</span> git merge --no-ff release-1.2
<span class="go">Merge made by recursive.</span>
<span class="go">(Summary of changes)</span>
</pre></div>

This step may well lead to a merge conflict (probably even, since we have changed the version number). If so, fix it and commit.

Now we are really done and the release branch may be removed, since we don’t need it anymore:
<div class="codehilite"><pre><span class="gp">$</span> git branch -d release-1.2
<span class="go">Deleted branch release-1.2 (was ff452fe).</span>
</pre></div>
