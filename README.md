# Git

- toc
  - [working in local](#local)
  - [working with remote](#working-with-remote)

## Local

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

- see the stashes list:

  ```shell
  git stash list
  ```
  
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

- how to delete a branch:

  ```shell
  git branch -d <branch-name>
  ```

  ```shell
  git branch -D <branch-name>
  ```

  > `-D` is equal to `-fd`!
  
## Remote

- see git current server remotes

  ```shell
  git remote -v
  ```
  