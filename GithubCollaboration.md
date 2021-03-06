Github Collaboration
================
Emily Bean
8/12/2020

# Protocols for Collaborating with the GandaLab Github account

This protocol describes how members of the lab should interact with the
GandaLab Github account for storing finished code and data on Github.
Also consult this blog post:
<https://blog.scottlowe.org/2015/01/27/using-fork-branch-git-workflow/>

## Terminology:

**GANDALAB** = GandaLab repo at this URL: <https://github.com/gandalab>

**REPO** = GandaLab repository of interest (for example: general-info)

**YOU** = Your Github URL

### Make a Github account and connect Git to RStudio

This is described in the “Git Started with Git” section under the
GandaLab README.md

### Fork the GandaLab repo of interest

At the GANDALAB page, navigate to the REPO and click “Fork”. This
creates a clone of the REPO and creates a local REPO in YOU (your
Github).

Navigate to the REPO stored in YOU (your Github). The URL should look
something like: `github.com/YOU/REPO`.

Click the green “Code” button and copy the URL of the REPO to your
clipboard. Open RStudio and create a new project. Checkout the project
from Version Control and select “Git”, then paste the REPO URL.

It is “best Git practice” to always work within a branch that is NOT the
master branch. This will help you if you need to roll back any mistakes.

To create a new branch to work in, open the Terminal window in RStudio
and type `git checkout -b BRANCHNAME`. This creates a branch AND adds
you to the branch.

### Set GandaLab as the upstream repo to get master changes

Github does not automatically recognize GANDALAB as the upstream repo
when you fork it. This is unintuitive, but you must take the extra step
in order to pull upstream changes.

First, type `git remote -v`. You should see something like this: `origin
https://github.com/EmilyB17/amr-heavymetal.git (fetch)`  
`origin https://github.com/EmilyB17/amr-heavymetal.git (push)`

Then, type `git remote add upstream` followed by the URL of the master
repo. This should be something like: `git remote add upstream
https://github.com/gandalab/REPO`.

Type `git remote -v` again. You should see something like this: `origin
https://github.com/EmilyB17/amr-heavymetal.git (fetch)` `origin
https://github.com/EmilyB17/amr-heavymetal.git (push)` `upstream
https://github.com/gandalab/amr-heavymetal (fetch)` `upstream
https://github.com/gandalab/amr-heavymetal (push)`

Now, you should be able to type `git pull upstream master`. This
specifies that you’re pulling changes made from the “upstream” remote
and updating those changes in your local clone.

*Be sure to pull upstream before making any pull requests. This will
help us avoid merge conflicts.*

### Make your local changes and merge to GANDALAB/REPO

You should be working in your local branch (not the master branch). When
you complete your work, save the files. There are two ways to make
commits through RStudio; you can use the Terminal window, or you can use
the point-and-click option towards the top of the RStudio window.

There are 4 steps to making changes in a forked REPO:

**1. Staging changes**  
In the terminal, type `git add FILENAME`

**2. Commit changes**  
This stores the changes in Git. In the terminal, type `git commit
FILENAME -m "MESSAGE"`. Note that the `-m` allows you to add a text line
about the changes you are making. This is important - your commit
message should be detailed to let your collaborators know what you
changed.

**3. Push your local changes** You have commited changes locally, so the
next step is to push them to Github to *your local copy of the forked
REPO*. In the terminal, type `git push origin BRANCHNAME`.

**4. Make a pull request to merge your changes to GANDALAB** In a web
browser, navigate to YOU/REPO. You should see a line at the top that
says you have made recent edits, and a green button that says `Create
Pull Request`. Click on that and follow the steps to create a pull
request. This sends a request to the REPO owner (GANDALAB) and asks them
to merge your changes into the GANDALAB/REPO.
