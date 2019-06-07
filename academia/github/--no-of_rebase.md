

When starting work on a new feature, branch off from the develop branch.

<div class="codehilite"><pre><span class="gp">$</span> git checkout -b myfeature develop
<span class="go">Switched to a new branch "myfeature"</span>
</pre></div>

Finished features may be merged into the develop branch to definitely add them to the upcoming release:
<div class="codehilite"><pre><span class="gp">$</span> git checkout develop
<span class="go">Switched to branch 'develop'</span>
<span class="gp">$</span> git merge --no-ff myfeature
<span class="go">Updating ea1b82a..05e9557</span>
<span class="go">(Summary of changes)</span>
<span class="gp">$</span> git branch -d myfeature
<span class="go">Deleted branch myfeature (was 05e9557).</span>
<span class="gp">$</span> git push origin develop
</pre></div>

The --no-ff flag causes the merge to always create a new commit object, even if the merge could be performed with a fast-forward. This avoids losing information about the historical existence of a feature branch and groups together all commits that together added the feature. Compare:

![](https://i.stack.imgur.com/FMD5h.png)

. To keep your feature branch fresh and up to date with the latest changes in master, use rebase
Every once in a while during the development update the feature branch with the latest changes in master. You can do this with:
<pre><code class="hljs maxima">git fetch <span class="hljs-built_in">origin</span>
git rebase <span class="hljs-built_in">origin</span>/master</code></pre>

In the (somewhat less common) case where other people are also working on the same shared remote feature branch, also rebase changes coming from it:

<pre><code class="hljs maxima">git rebase <span class="hljs-built_in">origin</span>/PRJ-<span class="hljs-number">123</span>-awesome-<span class="hljs-built_in">feature</span></code></pre>
