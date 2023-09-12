---
title: "Intro to Version Control, Part 1: Git"
author: "Bolívar Aponte Rolón<br> Original author(s): William Wilber <br> and Steve Formel " 
date: "Last edited: September 12, 2023"
format: 
  html:
    toc: true
    toc-location: left
    toc-depth: 2
    number-sections: true
    number-depth: 1
    theme: lumen
    highlight-style: github
    code-overflow: wrap
    code-fold: false
    code-copy: true
    code-link: false
    code-tools: false
    code-block-border-left: "#0C3823"
    code-block-bg: "#eeeeee"
    fig-cap-location: margin
    linestretch: 1.25
    fontsize: "large"
    embed-resources: true
execute:
  echo: true
  keep-md: true
editor: 
  markdown: 
    wrap: 72
---



## Objective

This tutorial will teach you how to track your projects with Git and
collaborate through GitHub for Windows, Mac and Linux.

## Why version control?

Before we can collaborate through GitHub, we need to learn how to run
Git on our personal computers. Git is a "version control" tool that lets
users collaborate on files while keeping the file history intact so that
previous versions are never lost. This can be useful for
non-collaborative projects as well when we need to keep track of our
edits. There has been a recent interest and push for Ecology and
Evolutionary Biology (applicable to other fields as well) to use Git and
GitHub (and similar) to improve research workflows, collaboration,
transparency and open research. See [Braga et al.
(2023)](https://doi.org/10.1111/2041-210X.14108)

### Prerequisites

-   Install Git

-   Register an account on [GitHub](https://github.com/).

-   Download [GitHub Desktop](https://desktop.github.com/)

## Installing Git

Let's check if you have Git installed already (MacOS and Linux). Begin
by opening a command line through the Terminal (MacOS) or your Linux
distribution (Windows).

Check whether Git is installed with the command:

`git --version`

-   **In MacOS** this will automatically prompt you to install Git if it
    is not available. See
    [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
    for more details.

-   **In Linux** you may install git with the command:

`sudo apt install git-all`

This command may vary depending on your Linux distribution. See [this
link](https://git-scm.com/download/linux) for detailed instructions on
what command to use.

-   **Windows**: <https://gitforwindows.org/>

::: callout-note
<font size="4">For Windows users, you may also consider a Linux
environment which can be installed on Windows 10 computers. To install
Linux in Windows, follow the instructions provided
[here](https://docs.microsoft.com/en-us/windows/wsl/install-win10).
:::

## Initializing Git

First we will **configure Git with our GitHub account details**. GitHub
is a hosting solution that allows us to easily share our Git
repositories with other users.

To set your account details in git:

`git config --global user.name "Your GitHub username"`

`git config --global user.email "Your GitHub account email"`

Git can also operate independently of GitHub, or with other hosting
options such as BitBucket or GitLab.

We can also **set our default command line text editor** for Git. By
default, Git will use the Vim editor on the command line. Command line
text editors can be confusing for users who are not used to working in
this environment. I recommend using nano for those that are new to the
command line, but Vim provides a more robust experience for those that
are open to learning a new tool.

`git config --global core.editor "nano -w"`

`git config --global core.editor "vim"`

You can check your configuration with the command:\
`git config --list`

## Your first repository

A repository is where Git saves the old versions of our files. We make
repositories inside of the directory that we are working in. **Let's
start by making a new working directory**. I will provide command line
code for those that are new to working this way.

`mkdir GitTut`

`cd GitTut`

With these commands, we have made a "GitTut" directory to work in, and
then navigated into the directory with the "cd" command. Now that we are
in our working directory, we **create a Git repository with the
command**:

`git init`

To see our new repository in the directory, use the command:

`ls -a`

You will see an output like this:\
![Contents of new repo](images/output1.PNG)\

The ".git" directory indicates that a repository has been created for
your working directory. All subdirectories within your working directory
will also be backed up in this repository.

We can also **check the project status** with the command:

`git status`

You will see this output:\
![Status of new repo](images/output2.PNG)\
For now, this means all is good! We will be returning to this status
screen often.

## Tracking file changes

Now we are on to the bread and butter of using Git. Make sure that you
are still in your "GitTut" directory before proceeding. You can check
your current directory with the command `pwd`.

**Create a new text file** in your working directory:

`touch abstract.txt`

This command creates a new text file "text.txt" that can be opened with
the text editor of your choice, either at the command line or with a GUI
based editor like Word. Enter some text into the file, then exit nano
with ctrl+x. Nano will automatically prompt you to save when exiting.

Let's again **check the project status**:

`git status`

We now see:\
![enter image description
here](https://lh3.googleusercontent.com/BUplRELmLCzwiJb8Z2O0z8gdnk8n0OBR-wSiK42aCe2KgmgLPOAzW7pqZG5K-FbJFQivU27blEal)

We now have an untracked file, "text.txt". This simply means this file
is new to the directory and has not yet been added to the repository. We
can **track a new file** with the command:\
`git add abstract.txt`

Again, check the project status:\
![enter image description
here](https://lh3.googleusercontent.com/hG_LikP-Vj2XaWSAQ9Vj8ERNl4VaqHQFv9UNSZ5Tz_6IufdXJM213Vpy1BgK6vwrFfPW8178irAh)\
The new file is now being tracked but has not yet been "committed".

Committing a change is like preserving a sample. Each "commit" is a
preserved state of your project that can be recalled in the future. The
commit command will preserve any changes that have been "added" to the
staging area. Let's try.

We can **commit our changes** with the command:

`git commit -m "add a description here".`

The "descriptive message" should be a short and clear statement about
the changes that were made, so that it's easy to identify what changes
the commit is associated with later on.

After you've run this command, check your git status again and your
repository is now current with the status of your directory.

To **see a log of the commits we've made**, we can use the command:

`git log`

The output of this command will show you who made the commit, when the
commit was made, and the descriptive message you entered when you made
the commit.

Let's edit the file again to see how Git tracks changes between
versions. Open the text file and change the contents, then save the file
and close it. To **view the changes** between the edits you've made and
what was saved in your last commit, use the command:\
`git diff`

Look at the output of this command and understand where it's showing you
what has been removed and what has been added.

Let's commit this change before moving on:\
`git add abstract.txt`\
`git commit -m ""`\
`git status`

We can **control what files in our directory are added to any given
commit** with selective use of the add function. Let's make a new file
to see how this happens:

`touch newabstract.txt`

Now edit the text in both the first and second text files and save your
changes.

Add each file to the staging area and commit them individually. Once
you've done this, check your git status to see that your working
directory in synced with your most recent commit, and use git log to see
all of the changes you've done so far.

Your output should look something like this:\
![enter image description
here](https://lh3.googleusercontent.com/YVOwJqnyLY5iNxQMu6VR-Atd23ofFCj0wlouToNXcyRTYtNGE65hQ_YYFMGcttgJw2M-A5DB2ZMG)

## Comparing commits and returning old commits

Each commit in your git log has a unique commit ID. We can use these IDs
to **compare the changes that have been made between commits**. Let's
try this now. Copy the commit number of your first commit and then use
this command:

`git diff commit#`

You will get an extended log of what we saw previously with the diff
command, showing all of the changes that have been made since the first
commit.

This output shows us the mistakes we have made in painful detail. How
can we fix the problems that we've made for ourselves? We can r**estore
a desired version of a file** with the checkout command.

`git checkout commit# abstract.txt`

Woohoo! Let's commit this change so that the most recent commit contains
both versions of the commit we desire.

This is all we will cover on the core functionality of git today. There
is a more comprehensive tutorial on Git that this was adapted from on
the [Software Carpentry
website.](https://swcarpentry.github.io/git-novice/) I highly reccomend
working through the rest of it on your own or with a partner!

## Collaborating with GitHub

Now we're finally on to the part you came here to see. However, as you
see there is little left to learn! GitHub is merely a service that
allows us to easily share out git repos with our collaborators. We only
need a few more commands to translate working with Git to working with
GitHub.

You should all have GitHub accounts. Go to the GitHub repository for
today's lesson:\
<https://github.com/tulaneURF/10_23_2019>

![enter image description
here](https://lh3.googleusercontent.com/eXrquvG8G1CfAdKp7DQMFzu-x_qs-PN3H3WvdW6qJ4x4TQhjRDBZskTmJ9KhZbKN1IvuC-aT20FP)\
You want to **clone this repository** to your computer. To do this, copy
the HTTPS address given on the webpage (or if you know it you can just
type it in manually in the command line.

On the command line, navigate to a location on your computer that you
want to clone the repository to. To clone a repository:

`git clone https://github.com/tulaneURF/10_23_2019.git`

Now navigate into this new directory. Let's use `ls -a` and `git status`
to check that this directory has a git repository associated with it.

How does this local repository communicate with GitHub? It uses a
remote, which links it to the GitHub repo. We **can see what remotes are
associated with a repo** with the command:

`git remote -v`

This shows us the name of the remote and where it is addressed to.
Remotes tell git where to "push" and "pull" from.

Now we all have the same directory. How do we share the changes that we
make with each other? We will work with this repo the same as we would
any other, we just have to add one extra step at the end.

*I will show you one example first before you try.*

Now that I have pushed my commit up to GitHub, you will need to pull my
changes down so that you have the most recent commit. **This completes
the basic GitHub workflow:**

-   `git pull origin master` updates your repo to the most recent
    version.
-   Edit the files you wish to change.
-   `git add editedfile.extension` stages the modified files to be
    committed.
-   `git commit -m "commit message"` creates a commit from the staged
    changes.
-   `git push origin master` pushes the commit to GitHub so that your
    collaborators can pull your edits.

That's probably all we're getting through today! If we have time I can
show you how conflicts between commits are resolved and how to
initialize your own remotes. Thanks for coming!