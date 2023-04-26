1.Create a repository using GIT GUI
	or
  Go to your desired folder and hit =>	git init

2.Making a follow on files:
	single file: git add fileName.ext
	all files: git add .

3.Connecting to remote repository:
	git remote add origin <githubrepo link .git>

4.Making a file commit:
	git commit fileName.ext -m "info about your commit"

5.Pushing local file to remote repo:
	git push -u origin master

6.Pushing after changes(if changes are made in remote and your local is behind):
	git pull
  find and resolve the changes and then add -> commit -> push

7.New Branch Creation(Same copy of master branch and you can work on it):
	git checkout -b branchName 

8.Switching between branches:
	git checkout branchName

9.Merging branches:
  go to master branch
	git merge branchName 
	git push

10.Actvity log and branch infos:
	git log
	git status

11.View files:
	ls
	ls -a
	cat fileName.ext

12.Removing files from add(remove from stage):
	git restore --staged fileName.ext

13.Go back to a particular commit:
   Find commit id: git log
	git reset <commitId>

   Moving all uncommited files to stash and the particular commit files will be restored
	git add .
	git stash 

   Returning back after recent commit and restoring all uncommit files from stash:
	git stash pop
   
   Removing all uncommited files from stash:
	git stash clear	



