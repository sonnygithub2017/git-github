* Contents:
  * What Really Matters In This Section - 2min
  * Checking Out Old Commits - 7min
  * Re-Attaching Our Detached HEAD! - 6min
  * Referencing Commits Relative to HEAD - 4min
  * Discarding Changes With Git Checkout - 5min
  * Un-Modifying With Git Restore - 6min
  * Un-Staging Changes With Git Restore - 4min
  * Undoing Commits With Git Reset - 8min
  * Reverting Commits With...Git Revert - 6min
  * Undoing Changes Exercise - 10min


* Notes:
  * What Really Matters In This Section - 2min
  * Checking Out Old Commits - 7min
    * `git checkout <commit_hash>`
    * in detached HEAD state: HEAD is pointing to a commit, not a branch reference
      * examine the contents of the old commit. can't make and save changes
      * to make changes and save them:
        * create a new branch at the current commit: `git checkout -b <new_branch_name>`
        * reattach HEAD to a branch reference: `git checkout <branch_name>` or `git checkout -`
    * in normal state: HEAD is pointing to a branch reference, and the branch ref is
      * one step to create a new branch for the old commit: `git checkout -b <new_branch_name> <commit_hash>`
  * Referencing Commits Relative to HEAD - 4min
    * `HEAD` is a reference to the current commit
    * `HEAD^` is a reference to the parent of the current commit
    * `HEAD~2` is a reference to the grandparent of the current commit
    * `HEAD~3` is a reference to the great-grandparent of the current commit

  * Discard changes not committed (unstaged or staged): `
    * `git checkout HEAD <file>` or `git checkout -- <file>` (overwrite the file with the version in the last commit)
    * `git checkout HEAD~1 <file>` (overwrite the file with the version in the commit before the last commit)
    * NOTE: THE `HEAD` IS NOT MOVED, ONLY THE FILE IS OVERWRITTEN, `git log --oneline` will show the same commits and HEAD location
  * Discarding Unstaged Changes (in working directory)
    * `git restore <file>` (discard changes in unstage changes)
  * Un-Staging Changes (move changes from stage to unstage)
    * `git restore --staged <file>`
  * Undoing Commits With Git Reset
    * `git reset HEAD~1` (both HEAD and branch ref back one commit, changes are still in working directory) - so you can make changes and commit again
    * `git reset --hard HEAD~1` (both HEAD and branch ref back one commit, changes are discarded) --- **DANGEROUS**
  * Reverting Commits With...Git Revert - 6min
    * once your commit is pushed to remote, you can't remove it with `git reset`, only add a new commit that undoes the changes
    * change1 -> change2 -> change3 -> revert-change1
    * Steps:
      - Sync with remote: `git pull origin main`
      - Find commit-id (full or short) of plan-to-revert: `git log --oneline`
      - Add a new commit to revert old-commit: `git revert <commit-id>`
      - If conflict, resolve it manually, then `git add <f1> <f2> <f3>` and `git revert --continue`
      - This will create a new commit that undoes the changes of the old commit
      - Push changes: `git push origin main`(github) or `git push origin HEAD:refs/for/master`(gerrit)