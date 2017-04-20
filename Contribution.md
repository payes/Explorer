# Contribution Guide

To contribute openebs/maya firstly, you have to fork the openebs/maya repository. In any case, before you start working on your issue, sync 
your repository with the upstream openebs/maya master. Syncing ensures your repository has the latest changes.

### To sync your repository:
Open a terminal on your local host. Change directory to the maya-fork root.

```sh
$ cd ~/repos/maya-fork
```

 Checkout the master branch.

 ```sh
 $ git checkout master
 Switched to branch 'master'
 Your branch is up-to-date with 'origin/master'.
 ```
 
 Recall that origin/master is a branch on your remote GitHub repository.
 Make sure you have the upstream remote openebs/maya by listing them.

 ```sh
 $ git remote -v
 origin	https://github.com/prateek/maya.git (fetch)
 origin	https://github.com/prateek/maya.git (push)
 upstream	https://github.com/openebs/maya.git (fetch)
 upstream	https://github.com/openebs/maya.git (push)
 ``` 
	 
 If the upstream is missing, add it by using below command.

 ```sh
 $ git remote add upstream https://github.com/openebs/maya.git
 ```
 Fetch all the changes from the upstream master branch.

 ```sh
 $ git fetch upstream master
 remote: Counting objects: 141, done.
 remote: Compressing objects: 100% (29/29), done.
 remote: Total 141 (delta 52), reused 46 (delta 46), pack-reused 66
 Receiving objects: 100% (141/141), 112.43 KiB | 0 bytes/s, done.
 Resolving deltas: 100% (79/79), done.
 From github.com:openebs/maya
   * branch            master     -> FETCH_HEAD
 ```

 Rebase your local master with the upstream/master.

 ```sh
 $ git rebase upstream/master
 First, rewinding head to replay your work on top of it...
 Fast-forwarded master to upstream/master.
 ```
 This command applies all the commits from the upstream master to your local master.

 Check the status of your local branch.

 ```sh
 $ git status
 On branch master
 Your branch is ahead of 'origin/master' by 38 commits.
 (use "git push" to publish your local commits)
 nothing to commit, working directory clean
 ```
 Your local repository now has all the changes from the upstream remote. You need to push the changes to your own remote fork which is origin master.

 Push the rebased master to origin master.
 
 ```sh
 $ git push origin master
 Username for 'https://github.com': username
 Password for 'https://username@github.com':
 Counting objects: 223, done.
 Compressing objects: 100% (38/38), done.
 Writing objects: 100% (69/69), 8.76 KiB | 0 bytes/s, done.
 Total 69 (delta 53), reused 47 (delta 31)
 To https://github.com/username/maya.git
 8e107a9..5035fa1  master -> master
 ```

 Create a new feature branch to work on your issue.
 Your branch name should have the format XX-descriptive where XX is the issue number you are working on. For example:

 ```sh
 $ git checkout -b xx-fix-dep
 Switched to a new branch 'xx-fix-dep'
 ```

 Your branch should be up-to-date with the upstream/master. Why? Because you branched off a freshly synced master. Let’s check this anyway in the next step.

 Rebase your branch from upstream/master.

 ```sh
 $ git rebase upstream/master
 Current branch fix-dep is up to date.
 ```
 At this point, your local branch, your remote repository, and the `maya` repository all have identical code. You are ready to make changes 
 for your issue.