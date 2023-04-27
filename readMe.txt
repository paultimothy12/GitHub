1.Create a repository using GIT GUI
	or
  Go to your desired folder and hit =>	git init

2.Making a follow on files:
	single file: git add fileName.ext
	all files: git add .

3.Connecting to remote repository:
	git remote add origin <githubrepo link .git>

4.Making a file commit:
	git commit -m "info about your commit"

5.Pushing local file to remote repo:
	git push -u origin master

6.Pushing after changes(if changes are made in remote and your local is behind):
	git pull
  find and resolve the changes and then add -> commit -> push
  	git push -u origin master -f

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

   Moving all current uncommited files to stash and the particular commit files will be restored
	git add .
	git stash 

   Returning back after recent commit and restoring all uncommit files from stash:
	git stash pop
   
   Removing all uncommited files from stash:
	git stash clear	

14.Delete commits until a particular commit:
   Follow step 13 until git stash,
	git push -u origin master -f

15.Multiple commits(Not Pushed) into Single commit:
	git rebase -i <commitId>
   Change the commits from pick to s, to commit as single commit
	pick <commitId1> message
	s <commitId2> message
	s <commitId3> message
	pick <commitId4> message
		Now, first three commits will be converted to single commit
	close env and set a message
   Now push 
	git push -u origin branchName(-f)

Working on existing repos:
Read before working,
  Fork the existing repo to your repositories
  Never work on master/main on repo, make new branches( 1PR/Branch )

1.Clone the existing repo to our local:
	git clone <repo link>

2.(Optional) Adding upstream:
	git remote add upstream <repo link>

3.Work with branches and push them, Send a PR from GitHub
   Now when upstream repo accepts the PR, upstream-master will be same as your fork-branch
   But your fork master will be behind upstream-master and fork-branch.	

	To Sync upstream-master and fork-master:
	git pull upstream master

		or
	git fetch --all --prune
	git reset --hard upstream/master
	git push -u origin master






