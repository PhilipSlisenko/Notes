**rebase** [option] HEAD~  
`~` points to parent so HEAD~ points to second last commit.  HEAD~1 third, etc.  
Options:  
- `--soft` deletes commit but retains changes in staging area and workdir  
- `--mixed` deletes commit, retains workdir  
- `--hard` deletes everything  

If you’ve made changes since the reset, using `git status` will also tell you that the local and remote branches have diverged. However, if you’re 100% sure, you can force the remote to reconcile with the local repository using `git push -f`  
***
**revert** HEAD~    
The command `git revert HEAD` creates a _new_ commit which reverses the actions of the last commit. 
***
**amend**  
If you have staged changes that you want to combine into the last commit, rather than make a new commit (this makes sense if the change is minor) then this command comes in pretty handy:  
```
$ git commit --amend
```
Additionally, use the  `-m`  flag if you wish to amend the commit message:
```
$ git commit --amend -m "Corrected commit message"
```
However, because Git actually replaces the last commit with a brand new commit, you’ll need to force-push the update to your remote. Again this isn’t ideal for shared remote repositories as there is a potential to create branch conflicts.  
```
$ git push -f
```