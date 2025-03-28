* Contents
  - What Really Matters In This Section - 2min
  - Introducing The Git Diff Command - 4min
  - A Guide To Reading Diffs - 10min
  - Viewing Unstaged Changes - 4min
  - Viewing Working Directory Changes - 3min
  - Viewing Staged Changes - 2min
  - Diffing Specific Files - 3min
  - Comparing Changes Across Branches - 5min
  - Comparing Changes Across Commits - 2min
  - Visualizing Diffs With GUIs - 6min
  - Diff Exercise

* Notes
  - A Guide To Reading Diffs - 10min
    - situation: have a newfile.txt with following contents:
      ```
      line 1
      line 2
      line 3
      ```
    - make changes to newfile.txt with content:
      ```
      line 1
      line 2
      line Three
      ```

    - `git diff` it will show following:
      ```diff
      diff --git a/newfile.txt b/newfile.txt      <--- 2 files to compare. a/ is the old file, b/ is the new file>
      index 3b18e7b..f3b3b3b 100644
      --- a/newfile.txt         <--- `a` file is ---
      +++ b/newfile.txt         <--- `b` file is +++
      @@ -1,3 +1,3 @@           <--- `a` start line1, 3 line to show.  `b` file start line1, show 3 lines
        line 1
        line 2
      -line 3                   <--- `a` file has line 3
      +line Three               <--- `b` file has line Three
      ```
  - Viewing Unstaged Changes - 4min
    - `git diff`
      - shows the difference between unstaged changes and staged changes
      - if no staged changes, it shows the difference between working directory and last commit -- see above example
  - Viewing Staged Changes - 2min
    - `git diff --staged`
      - shows the difference between staged changes and last commit
  - Viewing changes in unstaged + staged vs. last commit
    - `git diff HEAD`
  - Diffing Specific Files - 3min
    - `git diff newfile.txt`
    - `git diff newfile.txt newfile2.txt`
    - `git diff --staged newfile.txt`
    - `git diff HEAD newfile.txt`
    - `git diff HEAD newfile.txt newfile2.txt`
    - `git diff HEAD~2 newfile.txt`
    -
  - Comparing Changes Across Branches - 5min
    - `git diff master..feature`
    - `git diff master..feature newfile.txt`
  - Comparing Changes Across Commits - 2min
    - `git diff 1234567..abcdefg`
    - `git diff 1234567..abcdefg newfile.txt`
  - Visualizing Diffs With GUIs - 6min
  - Diff Exercise