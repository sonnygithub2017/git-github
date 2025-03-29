* github single branch workflow
  - all developers work on the same branch
  - all developers push/pull their changes to the same branch
  - master branch will become a mess
  - much times spent on merging conflicts
* github multiple branch workflow
  - always keep the master branch clean
  - all developers work on their own feature branch without affecting others
  - this feature branch can independently collaborate with other developers (get review, modify, etc.), even if the feature is NOT done.
  - when that feature is done, merge the feature branch into master branch
  - delete the feature branch after merging
  - example workflow:
    - your team members have a `feature` branch in github, want people to review and help for issue
    - you can do following:
      - get all remote branches: `git fetch origin`
      - create a new branch for the feature: `git checkout -b feature origin/feature` or `git switch feature`
      - review the code and modify it
      - add and commit the changes: `git add <file>` and `git commit -m "message"`
      - push the changes to remote: `git push origin feature`
    - your team member can get the changes and review it
      - `git checkout feature` or `git switch feature`
      - `git pull origin feature` to get the modified changes
* merge feature to main branch
  - option 1: merge the feature branch into master branch locally, then push to remote
    - get latest changes of feature from remote: `git checkout feature` and  `git pull origin feature`
    - get latest changes of master from remote: `git checkout master` and `git pull origin master`
    - merge the feature branch into master branch: `git merge feature`
    - push the changes to remote: `git push origin master`
  - option 2: Pull Request (more common) --- for review and merge feature branch into master branch

* pull request (PR)
  - workflow:
    - do some work locally on a feature branch
    - push the feature branch to github
    - github: create pull request (PR)
      - "Pull requests" > "Create pull request"
      - choose the base branch (master) and compare branch (feature)
      - add a title and description for the PR
      - assign reviewers (team members) to review the PR
      - PR page: https://github.com/<acct-name>/<repo>/pull/<num>, like  https://github.com/sonnygithub2017/cheatsheets/pull/5
    - your team members can review the PR and add comments, back and forth
    - NOTE: the PR will be the same if it is not closed/merged and they are the same base and compare branches
    - after the review, you or dedicate member can merge it (Merge pull request, or squarsh and merge ) on github
    - after the merge, you can delete the feature branch in github
  - Handle conflict when merge PR
    - update master branch: `git checkout master` and `git pull origin master`
    - get latest changes of feature from remote: `git checkout feature` and  `git pull origin feature`
    - merge master into feature branch: `git merge master`
      - resolve the conflicts manually
      - add and commit the changes: `git add <file>` and `git commit -m "message"`
    - push the changes to remote: `git push origin feature`
    - this changes and commit will be added to the PR,
    - in github, you can merge the PR (from feature to master) after the review
* configure branch protection:
  * set some rules for the branch, like
    - require pull request reviews before merging, and number of reviewers
  * github > repo > settings > branches > branch protection rules > Add classic branch protection rule
    - Branch name pattern: `main`
    - check "Require a pull request before merging"
    - check "Require approvals" and set the number of reviewers
* fork
  - For repo that you are not collaborator, but want to contribute to an open source project.
  - in github: create a copy of the repo in your own github account, so you can make changes
    - original repo: https://github.com/Shubhamsaboo/awesome-llm-apps
    - forked repo: https://github.com/sonnygithub2017/awesome-llm-apps (forked from Shubhamsaboo/awesome-llm-apps)
  - workflow:

      Github:              original repo:
                        ^   m1 - > m2 - > m3 - > m4
                   PR /               (upstream)
                    /                   |
                forked repo             |
                    \ (origin)          |
      ----------------\-----------------|-------------
      local machine:    \ push          | Pull
                          \             v
                            m1 - > m2 - > m3 - > m4
                            (local repo)
      ```mermaid
      flowchart TB
          subgraph group1 [GitHub]
              direction RL
              A["Original Repo (upstream)"]
              B["Forked Repo (origin)"]
          end

          subgraph group2 [Local Machine]
              direction TB
              C[Local Repo]
          end



          A --fork--> B
          B --"Pull Request"--> A
          A --"(upstream) Pull"--> C
          C --"Push (origin)"--> B
      ```

    - fork the repo in github
    - in local machine, clone the forked repo with `git clone <forked_repo_url>`, - `origin` is the forked repo
    - add the original repo as a remote: `git remote add upstream <original_repo_url>` - `upstream` is the original repo
    - make changes and commit them
    - rebase or merge the changes from the original repo to your forked repo
      - `git checkout main` to switch to the main branch
      - `git pull upstream main --rebase` to rebase the changes from the original repo to your forked repo
      - `git pull upstream/main`  to pull the changes from the original repo to your forked repo
      - if there are conflicts, resolve them manually, then `git add <file>` and `git rebase --continue` or `git merge -m "message"`
    - push the changes to your forked repo: `git push origin main`
    - in github: create a pull request from your forked repo to the original repo
      - base repo: original repo
      - base branch: main
      - head repo: your forked repo
      - head branch: main
      - add a title and description for the PR
    - original repo owner can review the PR and merge it

