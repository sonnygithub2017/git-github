* remote tracking branch
  - github:
                           (master)
      commit1 <- commit2 <- commit3
  - local:
    - `git clone <url>`: clone a repo from github

                            (master)
      commit1 <- commit2 <- commit3
                          (origin/master)
    - origin/master is a remote tracking branch, it tracks the remote branch last time you communicate with github
  - if add a new commit in local,
    - the origin/master will not move, only the master will move
                                      (master)
      commit1 <- commit2 <- commit3 <- commit4
                        (origin/master)
    - `git status` will show "Your branch is ahead of 'origin/master' by 1 commit"
    - `git checkout origin/master` you will be in detached HEAD state, you can look around the changes in origin/master
    - `git checkout master` you will be back to master branch
    - `git push origin master` will push the changes to github, and origin/master will move to the new commit
* github have multiple branches, like main, feature, etc.
  - github
                          (master)
    commit1 <- commit2 <- commit3
                  \
                  commit4 <- commit5
                              (feature)
  - local:
    - `git clone <url>`: clone a repo from github
      - NOTE: all the remote branches are download into local repo, but only master branch is checked out (active)
      - `git branch`: will show only master branch, not feature branch
      - `git branch -r`: will show all remote branches, like
        - origin/master
        - origin/feature
      - `git log --oneline --all --graph`: will show all branches and commits
    - `git checkout -b feature origin/feature` or `git switch feature`:
      - create a local branch `feature`, and switch to it (active), and link it to origin/feature
    - `git branch`: will show `master` and `feature` branches

* git fetch and git pull

          | git add -> | git commit -> | git push ->  |
          |            |               |              |
          |            |               |              |
      Workspace     Staging        Local Repo       Remote Repo
          |            |               |              |
          |            |               |              |
          |            |               | <- git fetch |
          |  <--------  git pull  --------------------|
          |  <---- git checkout -------|

  - git fetch: download the changes from the remote repo to the local repo, but not merge them (not in the workspace)
    - `git fetch` or `git fetch origin`: download the all branch changes from the remote repo to the local repo
    - `git fetch origin master`: download only the master branch changes from the remote repo to the local repo

    - github:
                                                  (master)
      commit1 -- commit2 -- commit3 -- commit4 -- commit5
    - local:

                        (origin/master)
      commit1 -- commit2 -- commitx
                           (master)

      - `git fetch origin master`: download the master branch changes from the remote repo to the local repo

                        commit3 -- commit4 -- commit5
                       /                      (origin/master)
      commit1 -- commit2 -- commit_x
                           (master)
      - `git log --oneline --all --graph`:
        - HEAD is still pointing to master, and master is still commit_x (this is active branch)
        - you will have commit3, commit4 and commit5, and origin/master is moving to commit5
      - `git status` will show
          `Your branch and 'origin/master' have diverged,`
          `and have 1 and 3 different commits each, respectively.`
      - `git checkout origin/master`: you will be in detached HEAD state, you can look around the changes in origin/master
      - `git checkout master`: you will be back to master branch

  - git pull: download the changes from the remote repo to the local repo, and merge them (in the workspace)
    - it is a combination of `git fetch` and `git merge`, so which branch you are in is important, it will download the changes from the remote repo to the local repo, and merge them
    - `git checkout master`: switch to master branch
    - `git pull origin master`: download the master branch changes from the remote repo to the local repo, and merge them into the master branch
    - 3 situations for the merge during `git pull`:
      - fast forward merge: if the master branch is behind the origin/master branch, git will just move the master branch to the origin/master branch
      - 3-way merge: if there are changes in both master and origin/master, but no conflict. git will automatically create a new commit that merges the changes from both branches
      - conflict: if there are changes in both branches that conflict with each other, you will need to resolve the conflicts manually
    - short term:
      - `git pull`: if you are in the master branch, this is equivalent to `git pull origin master`