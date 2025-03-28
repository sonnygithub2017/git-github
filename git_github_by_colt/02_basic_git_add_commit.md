* Contents:
  1.  What Really Matters In This Section - 1min
  2.  What Is A Git Repo? - 4min
  3.  Our First Commands: Git Init and Git Status - 4min
  4.  The Mysterious .Git Folder - 4min
  5.  A Common Early Git Mistake - 4min
  6.  The Committing Workflow Overview - 6min
  7.  Staging Changes With Git Add - 7min
  8.  Finally, The Git Commit Command! - 5min
  9.  The Git Log Command (And More Committing) - 8min
  10. Committing Exercise - 8min

1.  Git Repo
   - Git repo is a folder with git for version control
   - each repo has it own history, branches, commits, etc.
2.  Git Init and Git Status
   - `git status`: show status of repo. e.g., untracked, modified, staged, etc.
     - must be within a git repo. if not, it will say `fatal: not a git repository (or any of the parent directories): .git`
   - `git init`: initialize a git repo in the current folder
     - it will create a `.git` folder in the current folder
     - and main/master branch
3.  .Git Folder
   - `.git` folder contains all the git info
   - it is hidden by default
   - if it is deleted, the repo is gone
4.  Common Git Mistake
   - git will monitor the entire folder and subfolders
   - you can run `git` commands in root or subfolders'
   - don't run `git init` again in same or subfolder, so already run `git status` before running `git init`
5.  Committing Workflow
   - commit: checkpoint or snapshot of changes
     - commit is different from "save files". save is basis, commit is above save, it is a record for checkpoint of changes
   - workflow:
     - make changes, create files: -- working directory
     - stage changes: -- staging area: put change in different bucket, so each bucket can be committed separately
     - commit changes: checkpoint the changes and store in local git repo
6.  Staging Changes - Git Add
   - working directory: where you make changes/create files, and save them. `ls` shows files in working directory
   - staging area: where you put changes or group changed files to be committed.
   - `git add file1 file2`: put file1 and file2 in staging area
   - `git add .`: put all files in staging area
7.  Git Commit
   - `git commit -m "message"`: commit changes in staging area
   - snapshot of the changes will saved in .git folder
   - Good commit message: short and descriptive, Use present tense, e.g., "Start file for reset_revert_restore.md"
8.  Git Log
  - `git log`: show commit history
  - `git log --oneline --graph`: show commit history in one line
9.  Committing Exercise - 8min