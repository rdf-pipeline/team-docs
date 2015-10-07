# Pipeline Team Git Cheatsheet

This documents the git command line steps used by the RDF-pipeline team development 
process.  For more information about git, please refer to the 
<a href="https://git-scm.com/documentation">Git documentation</a> or the 
<a href="https://git-scm.com/book/en/v2">Pro Git free book</a>.  There is also this 
helpful cheat sheet of useful git commands 
<a href="http://orga.cat/posts/most-useful-git-commands">useful git commands</a>.

## RDF Pipeline Team Approach to Git

Our team has agreed to the following approach: 
1. We will perform all work from a branch.
2. The developer will check in the code and create a pull request for review.
3. Other team members will try to review changes within 24 hours
4. Reviewed code will be merged into the master Code will 

We are not currently used forks or a developer branch but may revisit this decision
at a later date as the project matures.

There are some helpful git GUI tools available that simplify many of these steps 
including the <a href="https://desktop.github.com/">Github Desktop App</a>, and 
<a href="https://www.sourcetreeapp.com/">Atlassian SourceTree</a>.

## Initial configuration

If you are going to use the git command line, these settings may be helpful:
```
  git config --global user.name "<your github user name>"
  git config --global user.email "<your email address>"
  git config --global push.default simple        # configure how push matches branches
  git config --global core.editor "<vi|vim|emacs>"   # set default git editor
  git config --list                              # check config settings
```

## Checkout a repository

1. Clone the repository
    ```
    git clone https://github.com/dbooth-boston/rdf-pipeline.git rdf-pipeline
    ```

2. Checkout a branch 
    ```
    git checkout -b master
    ```

3. Verify your branch 
    ``` 
    git branch
    ``` 

## Commits and Pull Requests

 
1. Review the files you are changing to be sure it is as you expect
    ```
    git status
    git diff
    ```

2. Stage your files for commit
    ```
    git add <filename>
    ```
    Repeat for each file

3. Commit the change to your branch
    ```
    git commit -m "a commit summary message about the change"
    ```

4. Pick up the latest code and merge with your branch if needed 
    ```
    git pull origin master
    ```

5. Push your changes to our remote to make it visible to others:
    ```
    git push origin <your branch>
    ```

6. Create a pull request
 
    Although it is possible to create a pull request from the command line, 
    it is easier to your browser, point it to your repository (e.g., 
    https://github.com/rdf-pipeline/team-docs) and click on the 
    **Compare & Pull Request** button that you will see after pushing an update. 

    From the pull request window: 
    * Verify your changes look correct
    * Fill in a description of the changes 
    * Assign the appropriate engineers on the team to review (using the _assignee_ option on the right) 
    * Click the **Create Pull Request** button 

    Your assignees will automatically be notified and the change will be posted
    to the Github channel on slack.

## Merging to master

After your code review, the following steps should be done: 
1. If your branch now has multiple commits, squash it to one commit to make tracking
   project history easier: 
    ```
    git log    # Check the local history to see how many commits you need to squash
    git rebase -i HEAD~<number of commits to squash>
    git log    # Verify the history looks correct before proceeding
    ```

2. Push the squashed version 
    ```
    git push
    ```

3. Go to the browser and point it to the repository you have modified 

4. Click the **Pull Requests** link on the right side of the page and select your
   pull request. 

5. Verify that the pull request can be merged. 

6. If it can be merged, click the button to do so.  If it cannot, you will need to
   return to your branch and enter: ```git pull origin master```, merge and resolve any
   conflicts, and repush.
