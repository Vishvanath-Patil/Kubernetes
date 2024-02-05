GIT
# Repositories: Repositories in GIT contains a collection of files of various versions of a project.

## 1. Is GIT a centralised or distributed version control s/m  (VCS) ? what is the diff
ans:  distributed 
In centralised VCS, you have client and server architecture & server is the remote repository which has all the copies of your code (ex: SVN ). But in distributed VCS every developer has all the versions of the code (gitlab, github,bitbucket). 
 
## 2. what are the GIT commands that you use to commit changes to your remote repository ?
Ans: git add
     git commit 
     git push

## 3. what is the difference b/w git fetch and git pull ?
Ans: git fetch: it only informs you about latest changes that are made to your remote repo, but it doesnot merge the changes to your local repository
git pull also does the same but it will merge the changes to your local repository.

## 4. what is the difference b/e git merge and git rebase ?
Ans: Both are designedto do the same purpose, If you want git history the go for git rebase, it gives a linear code history.
If you dont bother about your history then go for git merge.

## 5. What if the diff b/w .git and .gitignore ?
Ans: .git folder contains all the info like project details, file info related to your commit, remote repository adresses.
.gitingnore - if you want to ignore anything from .git simply go and put that file info in ths folder.

## 6. what are pre-commit hooks and post-commit hooks ?
Ans: hook means if you want to perform an action before or after something then it is called hook.
pre-commit hooks --> actions that are taken before you do git commit. 
post-commit hooks --> actions that are taken after you do git commit.  

## 7. what is web hook ?
Ans: if you want to trigger a pipeline or run python/ java program after your git commit, simply you configure a web hook
If you configure this, git hub will do the action you told it.
you can perform web hooks after issues  
you can perform web hooks after pull request
you can perform web hooks after issue commands

## 8. what is git stash & tell about its use cases ?
Ans: Git stash is used to save the changes temporarily you made to your working copy.
Suppose you are working on a bug in the code suddenly you got one more serious bug and now you want to move to that bug but can't commit these changes because the code is not ready, by that time you want to save the changes you have done to your current working code we do git stash. Then go to one more bug clear it, come back and do git stash pop, you will get those changes back.
 
## 9. diff b/w git clone and git fork ?
Ans: git clone --> you are creating a copy of the code which is present in the remote repo.
     git fork --> getting the git repo into your namespace. taking whole git repo from someones account to your namespace(git repo)

## 10. whats is cherry-pick in git ?
Ans: If you made commit in xyz branch and if there are no merge conficts and you want whole commit to your branch we do cherry-pick.

## 11. How to amend commit in git ?
Ans: amending means add something to existing commit
Suppose if you have done something wrong with your commit or to fix the broken commit we use amend.

## 12. How do you fix the merge confict ?
Ans:Suppose If two developer working on the same file and one of the developer tried to commit the changes he made to the code, you will get the merge confict 
It will be resolved with collaboration with developers and discuss which code has to retain and which one to neglect.
 
## 13.  what is Git flow or branching strategy..?

## 14. Git flow is a branching model where we have multiple branches to store different vesrions of code.
	1. master/main branch ==> primary branch where our final codes are available
	2. Feature branch ==> Here all the development activities taken place. once the code is developed it will be merged with master branch
	3. Release branch ==> maintian to store build application in this branch
	4. hot fix branch ==> In case of severe issues we create these branches and once the issue got resolved we will merge it with master.T
