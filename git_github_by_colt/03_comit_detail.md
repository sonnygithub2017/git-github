* Contents:
  1. Matters In This Section - 2min
  2. Navigating The Git Documentation - 4min
  3. Keeping Your Commits Atomic - 6min
  4. Commit Messages: Present Or Past Tense? - 3min
  5. Escaping VIM & Configuring Git's Default Editor - 9min
  6. A Closer Look At The Git Log Command - 4min
  7. Committing With A GUI - 6min
  8. Fixing Mistakes With Amend - 5min
  9. Ignoring Files w/ .gitignore - 11min



1. Matters In This Section - 2min
2. Navigating The Git Documentation - 4min
  - http://git-scm.com > Documentation > Reference
3. Keeping Your Commits Atomic - 6min
  - Keep each commit focused on a single thing
4. Commit Messages: Present Or Past Tense? - 3min
  - Present tense, imperative style: "Fix typo in outline file" instead of "I fixed typo in outline file"
5. Escaping VIM & Configuring Git's Default Editor - 9min
  - used when commit have multiple lines of message
  - `git commit`  defaults to VIM
  - To change with vscode as editor:
    - place vscode (`code`) in system path: in vscode: command palette > Shell Command: Install `code` command in PATH
    - Terminal: `git config --global core.editor "code --wait"`
6. A Closer Look At The Git Log Command - 4min
  - `git log` to see commit history
  - `git log --oneline` for compact view
  - `git log --oneline --graph` for graph view
7. Committing With A GUI - 6min
  - like vscode "source control"
8. Fixing Mistakes With Amend - 5min
  - only for last commit
  - `git commit --amend` to add changes to last commit, or change commit message
9.  Ignoring Files w/ .gitignore - 11min
  - create `.gitignore` file in root of repo
  - add files/folders or patterns to ignore
  - like file: `.DS_Store`, folder: `node_modules/` or pattern: `*.log`