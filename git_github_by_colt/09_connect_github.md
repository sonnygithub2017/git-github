* Contents:
  * What Does Github Do For Us? 6min
  * Why You Should Use Github! 5min
  * Cloning Github Repos With Git Clone 8min
  * Cloning Non-Github Repos 3min
  * Github Setup: SSH Config 8min
  * Creating Our First Github Repo! 6min
  * A Crash Course on Git Remotes 7min
  * Introducing Git Push 9min
  * Touring A Github Repo 4min
  * Practice With Git Push 4min
  * A Closer Look At Git Push 6min
  * What does "git push -u" mean? 6min
  * Another Github Workflow: Cloning First 4min
  * Main & Master: Github Default Branches 6min
  * Github Basics Exercise


* Notes:
  * What Does Github Do For Us? 6min
    * github: a website that hosts git repositories
    * git: a version control system, a way to track changes to files
  * Why You Should Use Github! 5min
    * collaboration
    * THE home for open source projects
    * Exposure (Portfolio): show off your work
    * Backup: cloud storage
  * Cloning Github Repos With Git Clone 8min
    * make sure you are not in a git repo: check with `git status`
    * `git clone <url>`: clone a repo from github
    * cd into the new directory, `ls` to see the files, and `git log` to see the commit history
    * NOTE: `git clone` will NOT only for github repos, it will work for any git repo
    * NOTE: Not need permissions to clone a public repo, only `git push` or private repo will require permissions
  * Github Setup and authentication setup - for push or private repos
    * create account on github
      * username: any, this will be used later for your `git config --global user.name` or  `git config --local user.name`
      * email: any, this will be used later for your `git config --global user.email` or `git config --local user.email`
    * ssh access: add your public ssh key to github:
      * once configured, you don't need to enter your username and password every time you push to github
      * Steps:
        1) Check for existing ssh keys: `ls -al ~/.ssh`, if you see `id_rsa` and `id_rsa.pub` or `id_ecdsa.pub`, you have ssh keys
        2) Generate a New ssh key (if not keys exist):  `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"` -- this will create a new ssh key in `~/.ssh/id_rsa` (private-key) and  in `~/.ssh/id_rsa.pub` (public-key)
        3) Add private key to ssh-agent:
           1)  start ssh-agent to manage your keys: `eval "$(ssh-agent -s)"` and
           2)  add your private key to the ssh-agent: `ssh-add ~/.ssh/id_rsa`
        4) add your ssh public key to your github account: copy the contents of `~/.ssh/id_rsa.pub` and paste it into your github account under `Settings` -> `SSH and GPG keys` -> `New SSH key`
      * **remote for ssh** is `git@github.com:<username>/<repo-name>.git` like `git@github.com:sonnygithub2017/git-github.git`
    * https access: add PAT (Personal Access Token) from github to your `~/.git-credentials` file
      - create a PAT in GitHub: `Settings` -> `Developer settings` -> `Personal access tokens` -> `Tokens (classic)` -> `Generate new token` -> give it a name and select the scopes you want to grant this token -> `Generate token` -> copy the token and store it in a safe place
      - save the token in `~/.git-credentials` file: `echo "https://<username>:<token>@github.com" > ~/.git-credentials`
      - **remote for https** is `https://github.com/<username>/<repo-name>.git` like `https://github.com/sonnygithub2017/git-github.git`

  * connect to github workflow - Have local repo first
    * create a new repo on github, like `git-github` repo under your account
    * connect your local repo to github:
      * `git remote add origin <url>`, like https way: `git remote add origin https://github.com/sonnygithub2017/git-github.git`
      * `git remote -v`: check the remote connection
    * push up your changes to github:
      * `git push origin main`: push your local repo's main branch to the remote repo on github
      * `git push origin feature`: push your local repo's feature branch to the remote repo on github
  * Touring A Github Repo
    * branches in github: main, feature, bugfix, etc
    * switch to branches to see the files in that branch, and the commit history
    * click on the commits to see the changes in that commit (comparing with the previous commit)
  * Practice With Git Push
    * `git push <remote-name> <branch-name>`: push the changes in the branch to the remote repo on github
    * mostly remote-name is `origin` but you can have multiple remotes, like `upstream` for the original repo
  * A Closer Look At Git Push
    * `git push origin main`: push the changes in the main branch to the remote repo on github, it will create a new branch on the remote repo if it doesn't exist. If the branch exists, it will update the branch with the new changes
    * `git push origin feature`: push the changes in the feature branch to the remote repo on github, it will create a new branch on the remote repo if it doesn't exist. If the branch exists, it will update the branch with the new changes
    * `git push origin <local-branch>:<remote-branch>`: push the changes in the local branch to the remote branch on github, it will create a new branch on the remote repo if it doesn't exist. If the branch exists, it will update the branch with the new changes
  * What does "git push -u" mean?
    * `git push -u origin main`: -u is for upstream, it sets connection of remote and local branch, so next time you can just do `git push` without specifying the remote and branch, like `git push` or `git pull`
  * Another connect to Github Workflow: Cloning First
    * create a new repo on github, like `git-github` repo under your account
    * clone to local machine: `git clone <url>` like `https://github.com/sonnygithub2017/git-github.git`
      * local repo will be created and connected to the remote repo on github
      * `git clone <url>`: clone a repo from github.
      * `cd <repo-name>`: go into the cloned repo
      * `git remote -v`: check the remote connection
      * `git log`: will get all the commit history
    * you can now make changes, and commit them
    * push up your changes to github:
      * `git push origin main`: for main branch
      * `git push origin feature`: for feature branch
  * Main & Master: Github Default Branches
    * when first time create a repo on github, there is no branch
    * if you create file like `README.md` in github and commit, github will create a branch called `main` (default branch), but you can change it to `master` or any other name from the settings
    * if you initial your local repo first, you can change it like `git checkout main` and  `git branch -M master`
  * Github Basics Exercise