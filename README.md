#GitCommands



Translated Versions

A list of my commonly used Git commands

Getting & Creating Projects

Command	Description</br>
git init	Initialize a local Git repository</br>
git clone ssh://git@github.com/[username]/[repository-name].git	Create a local copy of a remote repository</br>

Basic Snapshotting
Command	Description

git status	Check status</br>
git add [file-name.txt]	Add a file to the staging area</br>
git add -A	Add all new and changed files to the staging area</br>
git commit -m "[commit message]"	Commit changes</br>
git rm -r [file-name.txt]	Remove a file (or folder)</br>

Branching & Merging
Command	Description

git branch	List branches (the asterisk denotes the current branch)</br>
git branch -a	List all branches (local and remote)</br>
git branch [branch name]	Create a new branch</br>
git branch -d [branch name]	Delete a branch</br>
git push origin --delete [branch name]	Delete a remote branch</br>
git checkout -b [branch name]	Create a new branch and switch to it</br>
git checkout -b [branch name] origin/[branch name]	Clone a remote branch and switch to it</br>
git branch -m [old branch name] [new branch name]	Rename a local branch</br>
git checkout [branch name]	Switch to a branch</br>
git checkout -	Switch to the branch last checked out</br>
git checkout -- [file-name.txt]	Discard changes to a file</br>
git merge [branch name]	Merge a branch into the active branch</br>
git merge [source branch] [target branch]	Merge a branch into a target branch</br>
git stash	Stash changes in a dirty working directory</br>
git stash clear	Remove all stashed entries</br>


Sharing & Updating Projects
Command	Description


git push origin [branch name]	Push a branch to your remote repository</br>
git push -u origin [branch name]	Push changes to remote repository (and remember the branch)</br>
git push	Push changes to remote repository (remembered branch)</br>
git push origin --delete [branch name]	Delete a remote branch</br>
git pull	Update local repository to the newest commit</br>
git pull origin [branch name]	Pull changes from remote repository</br>
git remote add origin ssh://git@github.com/[username]/[repository-name].git	Add a remote repository</br>
git remote set-url origin ssh://git@github.com/[username]/[repository-name].git	Set a repository's origin branch to SSH</br>
Inspection & Comparison
Command	Description
git log	View changes</br>
git log --summary	View changes (detailed)</br>
git log --oneline	View changes (briefly)</br>
git diff [source branch] [target branch]	Preview changes before merging</br>


-------------------------------------------------------------------------------------------------------------------------------
NAME</br>
git - the stupid content tracker</br>
