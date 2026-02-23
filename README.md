# Git

- toc
  - [Local](#local)
  - [Remote](#remote)

## General

- setup git on new machine
  - [LINK](https://gist.github.com/qin-yu/bc26a2d280ee2e93b2d7860a1bfbd0c5)

- node (commit) specifier
  - `HEAD` - current node
  - `HEAD~2`, `HEAD^^^`, `HEAD@{2}`, ... - current node before/after
  - commit id - node hash
  - `branchName` - indicator of last node of the branch

- branch specifier
  - `branchName`
  - `-` or `@{-1}` - previous branch

## Local

- git does not see `.gitignore` specified pathes

- changing levels
  - ignored
  - working tree
    - untracked
    - tracked
  - staged

### Changes

- having 2 file in 2 branch in same time with easy navigation
and easy changing each!
  - for this you can duplicate your git project with all
  git informations, one of this replicas is for navigation
  between different git nodes and watching them and another
  is for work that you currently on.

- we want to move our current change from current branch to
another branch!

  - first save your changes into the stash stack:

    ```shell
    git stash save
    ```

  - go to the branch you want:

    ```shell
    git checkout wantedbranch
    ```

  - pop your changes from stash stack:

    ```shell
    git stash pop
    ```
  
  - !!!! remember to pop your stash when you back to branch :/ !!!!

- see the stashes list:

  ```shell
  git stash list
  ```

- how to stash just single file

  ```shell
  git stash -- filename
  ```

  > if file is untracted first do to trackted :)
  
- removing current changes

  ```shell
  git restore path
  ```

- removing current changes added to stage

  ```shell
  git restore --staged path
  ```
  
- removing untrackted files

  ```shell
  git clean -fd
  ```

> -f means files, -d means directories

- remove files from git to add them to `.gitignore`

  ```shell
  git rm --cached path
  ```

- the only place that you can see the dangling commits!!!

  ```shell
  git reflog
  ```

### Branches

- when you create a branch, git make copies of the node that you are now on it.

- create new branch

  ```shell
  git branch branchname
  ```

- create new branch and switch on it

  ```shell
  git checkout -b branchname
  ```

- checkout to a commit

  ```shell
  git checkout commitspecifier
  ```

> when you checkout to a commit you are coding to a dangling branch!!! \
> Detached HEAD is a dangling branch
  
- how to delete a branch:

  ```shell
  git branch -d branchname
  ```

  ```shell
  git branch -D branchname
  ```

  > `-D` is equal to `-fd`!
  
- see logs of current branch

  ```shell
  git log --oneline prevbranch..
  ```

  ```shell
  git log --oneline prevbranch..HEAD
  ```
  
## Local as Remote

- exFAT filesystem problem only solution (**BUT SECURITY PROBLEM**)

  ```sh
  git config --global --add safe.directory "*"
  ```

- archive the git repo (considering .gitignore and ...)

  ```sh
  git archive --format=zip --output yourpath.zip yourbranch
  ```

- create git remote folder

  ```sh
  git init --bare repoRemote.git
  ```

  > you can use it just by cloning it, you can commit, push, anything ...
  
## Remote

- always try to have fast pull/push cycle!
- before push always pull changes (conflict in remote merging is not interesting!)
  - for this maybe you should first pull main branch and then merge it to your branch

> always try to push fast if you add or modify a `.gitignore` file!!!

- see git current server remotes

  ```shell
  git remote -v
  ```

- change remote

  ```shell
  git remote set-url origin new.git.url/here
  ```

- github remote format (ssh format)

  ```shell
  git@github:username/reponame.git
  ```

- remove a git branch from remote

  ```shell
  git push origin -d branchname
  ```

- git pull: connection refused!

  ```shell
  unset HTTP_PROXYFTP_PROXY ALL_PROXY NO_PROXY HTTPS_PROXY HTTP_PROXY FTP_PROXY
  ```

- if you have some commit ahead of remote main in your local main branch
  - create new branch from you local main
  - checkout from the local main
  - `git fetch origin`
  - `git checkout main`

### Conflict

- solve binary file conflict

  ```shell
  git checkout --theirs -- path/to/conflicted-file.txt
  ```

  ```shell
  git checkout --ours -- path/to/conflicted-file.txt
  ```

- push conflict (**DANGEROUS**)

  ```shell
  git push --force-with-lease
  ```
  
  - you should not use this command

    ```shell
    git push --force
    ```

- usually you can't search in commits by commit message directly in remotes like `github.com`
  you should clone the repo and search with below command:

    ```shell
    git log -g --grep=yourtext
    ```

  - after finding the commit id, you can go to search in remote site.
