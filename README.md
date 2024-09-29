# Git

- toc
  - [Local](#local)
  - [Remote](#remote)

## General

- node specifier
  - HEAD
  - HEAD~2, HEAD^3 ...
  - commit id (node hash)
  - branch name (indicator of last node of the branch)

## Local

- git does not see `.gitignore` specified pathes

- changing levels
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
    git checkout <wanted-branch>
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
  git stash -- <filename>
  ```

  > if file is untracted first do to trackted :)
  
- removing current changes

  ```shell
  git restore <path>
  ```

- removing current changes added to stage

  ```shell
  git restore --staged <path>
  ```
  
- removing untracted files

  ```shell
  git clean -fd
  ```

> -f means files, -d means directories

- remove files from git to add them to `.gitignore`

  ```shell
  git rm --cached <path>
  ```

### Branches

- when you create a branch, git make copies of the node that you are now on it.

- create new branch

  ```shell
  git branch <branch-name>
  ```

- create new branch and switch on it

  ```shell
  git checkout -b <branch-name>
  ```

- how to delete a branch:

  ```shell
  git branch -d <branch-name>
  ```

  ```shell
  git branch -D <branch-name>
  ```

  > `-D` is equal to `-fd`!
  
## Remote

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
  git push origin -d <branchname>
  ```
  
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
