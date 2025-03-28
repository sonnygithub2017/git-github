* Course content
  1. What Really Matters In This Section - 2min
  2. Introducing Branches - 6min
  3. The Master Branch (Or Is It Main?) - 5min
  4. What On Earth Is HEAD? - 6min
  5. Viewing All Branches With Git Branch - 1min
  6. Creating & Switching Branches - 8min
  7. More Practice With Branching - 5min
  8. Another Option: Git Checkout Vs. Git Switch - 5min
  9. Switching Branches With Unstaged Changes? - 4min
  10. Deleting & Renaming Branches - 6min
  11. How Git Stores HEAD & Branches - 5min
  12. Branching Exercise


* Notes

1. What Really Matters In This Section - 2min
2. Introducing Branches - 6min
   1. normally, git commits are linear, with each commit pointing to the commit that came before it (parent commit).

      ```mermaid
      graph TD
          node0[commit0 <br>parent: none <br>message: 'start files'];
          node1[commit1 <br>parent: commit0 <br>message: 'change files'];
          node2[commit2 <br>parent: commit1 <br>message: 'fix typo'];

          node2 --> node1 --> node0;
      ```
    2. If a context occurs (like new features or bug fixes), need to create different branch to work independently at the same time.
       |/
       |
    3. Branch has it own commit history, and not affect other branches.
    4. we can merge branches together to incorporate new feature.

3. The Master Branch (Or Is It Main?) - 5min
   1. master/main branch is the default branch in git. it is the branch that is created automatically  when you initialize a new git repository.
4. What On Earth Is HEAD? - 6min
   1. like `git log --oneline`,
      6d63de7 (`HEAD` -> `main`, `origin/main`) Revert "Create file3.txt"
      7728d64 Create file3.txt
   2. `HEAD`: A pointer for current location in the repository. At any given time, only one pointed by `HEAD` is active (in working directory).
   3. branch pointer: is a pointer to the latest commit in branch (tip of branch), above `main` in git log.
   4. normally `HEAD` points to a branch pointer, and branch pointer points to a commit.
   5. `HEAD` can also point to a commit directly, in detached HEAD state.
5. Viewing All Branches With Git Branch - 1min
   1. `git branch` to list all branches. `*` indicates the current branch.
6. Creating & Switching Branches - 8min
   1. `git branch <branch-name>` to create a new branch without switching to it.
   2. `git switch <branch-name>` to switch to a branch.
   3. `git checkout <branch-name>` to switch to a branch.
   4. `git checkout -b <branch-name>` to create and switch to a branch.
   5. `git switch -c <branch-name>` to create and switch to a branch.
   6. NOTE: the commits you get in new branch depends on the branch you are from.
7.  Switching Branches With uncommitted Changes? - 4min
    1.  if changes are existing files that not committed (unstaged or staged),
        1.  `git switch <branch-name>` will get error: Your local changes to the following files would be overwritten by checkout:
        2.  you need to commit or stash the changes first
    2.  if changes are new files (untracked),
        1.  `git switch <branch-name>` will work.
        2.  the new files will be in the new branch.
8.  Deleting & Renaming Branches - 6min
    1.  `git branch -d <branch-name>` to delete a branch.
    2.  `git branch -D <branch-name>` to force delete a branch (even if not merged).
    3.  `git branch -m <new-branch-name>` to rename a branch.  (on the branch you want to rename)
    4.  `git branch -m <old-branch-name> <new-branch-name>` to rename a branch.
9.  How Git Stores HEAD & Branches - 5min
    1.  The `HEAD` and branch references are stored in `.git` directory.
    2.  normally `HEAD` points to a branch ref, and branch ref points to a commit.
        ```
        % cat .git/HEAD
          ref: refs/heads/main         <-- main branch reference in HEAD (active branch)
        % cat .git/refs/heads/main
          6d63de7459c267fe93888ecf5caea0f1cb1850a5  <-- last commit in main branch

        if switch to feature branch:
        % cat .git/HEAD
          ref: refs/heads/feature       <-- feature branch reference in HEAD (active branch)
        % cat .git/refs/heads/feature
          cb55f1ce1f4b7f4b66d036764a2a21276fc838fd <-- last commit in feature branch
        ```

    3.  `HEAD` can also point to a commit directly, in detached HEAD state.
        ```
        % cat .git/HEAD
          00c6e9115cfbb1a28139332b51f543b88ee549d5  <-- commit reference in HEAD (detached HEAD)
        ```