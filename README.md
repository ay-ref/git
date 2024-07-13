# Git

- [working in local](#working-in-local)
- [working with remote](#working-with-remote)

## working in local

_**Problem.**_
having 2 file in 2 branch in same time with easy navigation
and easy changing each!

_**Solution.**_
for this you can duplicate your git project with all
git informations, one of this replicas is for navigation
between different git nodes and watching them and another
is for work that you currently on.

_**Problem.**_
we want to move our current change from current branch to
another branch!

_**Solution.**_

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

## working with remote
