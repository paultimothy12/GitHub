1.Create a repository using GIT GUI
	or
  Go to your desired folder and Hit => git init

2.Making a follow on files(selecting files to save):
	single file: Hit => git add fileName.extension
	all files: Hit => git add .
	
	Note:
	You can unselect them if you dont need to commit the changes for now
		Hit => git restore --staged fileName.extension
				OR
			git restore --staged .

3.Connecting to remote repository(connect your local repository to remote repository):
	Hit => git remote add origin <githubrepolink>

4.Making a file commit(saving selecting files):
	Hit => git commit -m "info about your commit"

5.Pushing commits(log-your activities) to remote repository(saving your activities and changes to remote repository):
	Hit => git push -u origin master
	
6.View all your activities:
	Hit => git log
	
7.Status of changes:
	Hit => git status  //You can see if any files are modified, if any files need to be commited, whether if your branch is clean and up to date.
		
8.Conflicts:
	(happens when you do a direct commit on remote and then you made a commit on local without having the earlier commit of remote in your local)
	
	Your remote repository have 5 commits and local repository have 5 commits, 
		but 5th commit of both repositories are different.
	Case 1:
	You want 5th commit of remote to be your 5th commit in local,
		Step 1: Remove your 5th commit of local repository
			Copy commit id of 4th commit,
			Hit => git reset --hard <commitId>	//removes all commits after 4th commit
		Step 2: Hit => git pull		//pulling all commits from remote to local ( commit from remote will be saved to local repository)
		
	Case 2:
	You want 5th commit of local to be your 5th commit in remote,
		Step 1: We have to force push the local to remote, reflecting all commits to remote
			Hit => git push -u origin master -f   //force pushing to remote
	
9.Going to a particular commit:
	You have 5 commits on both local and remote.
	
	You need to go to 2nd commit,
	
	Case 1:
		Hit => git reset <2nd commitId>
		Now all the commits between 2nd and 5th(recent) commit will be removed permanently and changes of 5th commit will still be available.
		You can push the changes(5th commit) to a seperate space called "stash". Hit => git add .; git stash
			
		You don't need those changes too, then Hit => git stash clear //changes in stash will also be cleared
		Now your local will have 2 commits, if you want the same in remote repository(5 commits to 2 commits), do force push.
			Hit => git push -u origin master -f
			
		-------OR-------
		
		Hit => git reset --hard <2nd commitId>	//all commits will be directly removed(3rd commit to 5th commit)
		Now your local will have 2 commits, if you want the same in remote repository(5 commits to 2 commits) do force push
			Hit => git push -u origin master -f
	
	Case 2:
		Hit => git reset <2nd commitId>
		Now all the commits between 2nd and 5th(recent) commit will be removed permanently and changes of 5th commit will still be available.
		You can push the changes(5th commit) to a seperate space called "stash" => git add .; git stash
		
		You want the changes back(only 5th commit/ recent commit), Hit => git stash pop
			Hit => git add .; git commit -m "commit message" //Now 5th commit will be saved as 3rd commit
	
		If you want to reflect all the activities of local to remote, do force push.
			Hit => git push -u origin master -f
	
	
10.Branches:
	You can see we have been using the word "master" for a while, it's the branch name/copy name inside your repository.
		Default branch:
			Case 1: 
			When creating a local repository, the default branch name will be "master" and 
				when pushing to remote the default branch name will also be "master"
			Case 2: 
			Not working on local git, But You created a remote repository and commiting to remote directly with the github website,
				default branch name will be "main" when doing a intial commit.
		  

	New Branch Creation(Same copy of master branch and you can work on it):
		Note: Make sure your default branch of local repository is up to date with remote default branch
		Way 1:
			Hit => git branch <branchName>   //creates a new branch
			       git checkout branchName 	 //switching to the new branch 
		Way 2:
			Hit => git checkout -b branchName  //creates a new branch and also switch to the new branch

11.Merging new branch to default branch:
	Go to default branch,
		Hit => git checkout <defaultBranchName>
		       git merge <branchName>	//merging all new activities to default branch
		       
		       If you want all changes to be reflected in remote, then Hit => git push -u origin  <defaultBranchName>

12.View files in your directory:
	View list of all files in your current directory:	Hit => ls
	View list of all files in your current directory with hidden files:	Hit => ls -a
	
	Check the content of any file:	Hit => cat fileName.ext


13.Multiple commits into Single commit:
	Hit => git rebase -i <commitId>
	A interactive editor opens up now, You can see the first few lines like  "pick <commitId> commitMessage"
	Click I to enter insert mode, Change the commits from pick to s, to commit as single commit
		pick <commitId1> message
		s <commitId2> message
		s <commitId3> message
		pick <commitId4> message
		
		Now all commits with s will be combined with a pick above them, first three commits will be converted to single commit
	Close the editor - Click Esc and then :x and another editor opens up and now enter a new message like before.
	
        Now push 
		git push -u origin defaultBranchName -f

						=====WORKING ON EXISTING PROJECTS=====

Step 1: Forking existing repository,
	Go to the existing repository on github website and fork the respository into your account using the fork button.
	Note: A copy of that repository will be available in your account under your profile.

Step 2: Cloning the repositoy,
	Go to the forked repository in your profile and click on code button and copy the repository link.
	Now making a local copy of this repository,
		Hit => git clone <forkedRepositoyLink>

Step 3: Create new branches, commit changes and push to remote,
	*IMPORTANT* NEVER WORK ON DEFAULT BRANCH

Step 4: To contribute your changes,
	Go to your forked repository on github and click on contribute button and create a pull request.
	(From your-forked-repository/newBranch To existing-repository/defaultBranch)
	
	Your PR will be accepted or rejected, if accepted the existing project default branch will be updated and commits will be saved.
	
	*IMPORTANT*
	If you want to contribute "again" with same repository, CREATE NEW BRANCH -> start working then create a new PR.
		
		existing-repository/defaultBranch will have extra commits 
		your-forked-repository/defaultBranch will be few commits behind of existing-repository/defaultBranch
		
		BEFORE CREATING NEW BRANCH:
			SYNC YOUR FORK by using Sync Fork button 
				so that your-forked-repository/defaultBranch will be up-to-date with existing-repository/defaultBranch
			
				OR
			Add Upstream(existing-repository):
				Hit => git remote add upstream <existing-repo link>
				       git pull upstream <defaultBranchName>
				
 






