# Free Code Camp Course - Git - 3h

## ep - introduction

- the software can fail after some changes so
for backing to the stable situations (checkpoints)
like games when you lose you can back to saved point
and keep going well
- this kind of tool is called versoin control system (vcs)
- in this course we learn git as a tool

- git usage
  - cli
  - gui

> don't use gui, just learn cli very well

- git vs github
  - git
    - application
  - github
    - service
    - also like bitbucket, gitlab, ...

- git official documentation is a jungle for learning,
it is just useful as a reference api

- repo (repository)
  - it is just like a folder of things

- check git installation

    ```shell
    git --version
    ```

## ep - git mechanism

- you can specify that git track which of you folders,
and each folder as a project tracked sperately as a repo by git

- for enabling git on your project folder (repo) you should go to
your project root folder then

    ```shell
    git init
    ```

- this command make a `.git` folder in root folder,
remember all of the data stored by git is in this folder

- you hardly need to change something in `.git` folder

- then you can see the status of the current git on project

    ```shell
    git status
    ```

- commit
  - checkpoint

- git mechanism  
    1. working dir
    2. git add
    3. staging area
    4. git commit

- add a file to staging area

    ```shell
    git add <filepath>
    ```

- remove a file from staging area

    ```shell
    git rm --cached <filepath>
    ```

- create a checkpoint (commit) (changes and message are required!)

    ```shell
    git commit -m "message of changes (very important)"
    ```

- see the logs

    ```shell
    git log --oneline
    ```

- each commit has a commit id (that is unique)
- for using from it, just enough to use from some first character to be unique

- every commit should just does just one atomic job
- so you should commit soon after some changes (based on your task)
- each task is contained many commits to achive

- git user configs for whole of system

    ```shell
    git config --global user.name "Mona Lisa"
    git config --global user.email "mona.lisa@art.is"
    ```

- `.gitignore`
  - is file that you specify what you don't want to be
    tracked in git at all
  - just work on new files
  - for previous file that added first you should remove them with
  `--chached` flag from stage

  - some examples
    - package files, like pipenv
    - big files like videos and images
    - secret data like api keys

  - you can use from template for using template of `.gitignore`
  based on your project

- git configuration file globally is in your user root folder with name `~/.gitconfig`
- git configuration file locally is in your `.git/config` project path

- there is a `hooks` folder in `.git` folder that is the scripts
that runs in some specific time like before/after commit or before/after push

## ep - branches

- you can isolate (packed) your changes sequence by branches
- git contains nodes that each nodes show state of codes to that time

- each branch specified with a name

- default branch is `master` in git, but for
some reason we always rename it to `main` branch with below command

- rename an existing branch

  ```shell
  git branch -M newname
  ```
  
- how to see current branch

  ```shell
  git branch
  ```
  
- how to create new branch

  ```shell
  git branch branchname
  ```

- branch is applied to the current node
  
- change current branch

  ```shell
  git checkout branchname
  ```

- you can change the branch just if you have no change currently
  
> when we say that we are in main branch we usually
> mean that we are in the last node of main branch!,
> and a node in one branch is different and also you can
> checkout to it by its id!

- `HEAD` is the specifier for current node of changes

- merge
  - fast forward
  - not fast forward

- fast forward merge
  - when we merge with a target branch that is not changed after creation of
  current branch our history is linear!
  - in fast forward merge we have not any ***conflicts***
  - ***it does not make new merge commit***

- not fast forward merge
  - target branch and also current branch both
  has some changes and usually it is possible to have
  some ***conflicts*** and we should merge manually and then commit!
  - ***it makes new merge commit***
  - merge commit is a common commit for both branch (target and the current)!

- delete a branch

  ```shell
  git branch -d branchname
  ```

- see the changes during time

  ```shell
  git diff filepath
  ```
  
- you should consider the scope that you want to run your command
- usually command as default runs in ***working tree tracked files***
- for running command on staged mode you should specified `--staged`
  - examples

    ```shell
    git diff --staged
    ```

- `git diff` does diff between one file over time!
- linux `diff` command does diff between 2 different file in same time!

- git diff compare 2 files a(old) and b(newer)
  - `-` shows the file a
  - `+` shows change in file b

- git diff between 2 nodes

  ```shell
  git diff firstid..secondid
  ```
  
- when you want to fix a tiny bug in another branch
but your current branch changes are not commitable yet
you should use stash

- stash your current changes (staged and tracked working tree)

  ```shell
  git stash
  ```

- backing changes

  ```shell
  git stash pop
  ```
  
- see the stash list

  ```shell
  git stash list
  ```
  
- remove all current changes without saving it!

  ```shell
  git restore filepath
  ```
  
## ep - rebase :/

- you can add a branch changes to another branch
with
  - merge
  - rebase

- rebase in first glance is dangerous,
because it rewrite history!

- rebase adds your current branch history to target branch
and make target linear by current branch history changes

- !!!! the dangerous approach is where you are in main/master
branch and run rebase command !!!!

- rebase command should run from side branch

- merge a branch into another branch (go to your changed branch)

  ```shell
  git merge targetbranch
  ```

- rebase a branch in another branch (go to your changed branch)

  ```shell
  git rebase targetbranch
  ```
  
- rebase is possible to get into conflict then you should
consider one of below commands to make rebase complete

  ```shell
  git rebase --continue
  git rebase --skip
  ```

## ep - github

- you should create account
- for your account you should create sshkey
to connect your repositories by [LINK THAT IS HERE](https://gist.github.com/qin-yu/bc26a2d280ee2e93b2d7860a1bfbd0c5)
- make a repository

- commands

  ```shell
  git clone repourl
  ```

  ```shell
  
  ```
  