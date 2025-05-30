---
title: 'Getting Started with Git'
date: 2025-05-28
permalink: /tips/git/
author_profile: true
---

Understanding and being able to use git version control is an essential skill, but it can be daunting at first.  In our research lab, we will use git repositories to host all relevant codes and text files.  This serves two purposes.  First, it offers version control, which is very useful in our line of work (for example, if you accidentally introduce a bug into your code, you have an easily accessible record of your code "pre-bug").  Second, it allows us to conveniently share files and work in tandem.  I prefer to use Bitbucket repositories, but Github repositories work very similarly.

As a preliminary step, you should get comfortable using the terminal/command line.  Familiarize yourself with basic terminal commands like `cd` (change directory), `ls` (list files), and `mv` (rename file).  As a bonus, download an editor like `vim` and practice editing files from the terminal.  At the start you may only use the terminal to navigate git, but later on it may be essential for things like bash scripting, parallel computing, remote access, and utilizing supercomputers.  [While there are some GUI's for git that enable you to avoid the command line, I do not recommend these.  The command line is an important tool, and now is as good a time as ever to learn how to use it.]

To get started with a git repository, complete the following (these are things you should only have to do once).

1. Download git [here](https://git-scm.com/downloads).  You can check whether git has been installed by running the `git` command in the terminal.  If it is set up, you should see a list of usage and commands.

2. Set up SSH keys so that you can easily push/pull to private repos.  This involves connecting an SSH key for your machine to your Bitbucket/Github account.  Instructions for Bitbucket are available [here](https://support.atlassian.com/bitbucket-cloud/docs/configure-ssh-and-two-step-verification/).  

3. Clone the repository using the `git clone` command.  On Bitbucket, you may simply click the `Clone` button in the upper right corner and copy/paste the command into your terminal.  Afterwards, you will have a local version of the repository on your machine.

Basic Commands
------

There are tons of things you can do with git, but the following 5 commands are the essentials.  While I encourage you to familiarize yourself with other git functionality, you could probably get through your entire dissertation work with only these 5 commands.  *These are commands that you will run in the terminal from within the repository's directory.*

* `git pull`: This command pulls all changes that may have been pushed to the repository down to your local machine.  **Run this every time you start a new bout of work.**  If you're the only person actively working in a repository, this may seem extra, but it is nevertheless important to develop the habit.
* `git status`: This command is your best friend.  It will show you where your local work stands in relation to the repository.  Use this to check if all of your local work has been successfully pushed to the repository.
* `git add filename`: If `git status` shows that a file has local changes which you would like to push to the repo, you must first "add" this particular file with this command.  You may add an entire folder with `git add foldername/`.  If you do this, be careful that you do indeed want to add every file in that folder (check for hidden files).  I do not recommend using `git add -A` which adds every single file; in my experience, this results in a lot of unnecessary files being pushed (more on this below).  The `git status` command allows you to see all the files that have or have not been added.
* `git commit -m "message"`: After adding files, use this command to tell git that you are done adding and are ready to send things on to the repo.  **Include a descriptive message** which conveys what you worked on since the previous commit.  Sometimes I get lazy with this myself, but descriptive messages will help you down the line when you need to refer back to previous commits.  For example, the message "changed n from 25 to 50 for satellite simulation" is much better than "new n".
* `git push`: After adding and committing, use this final command to "push" your changes to the repository.  Then if you access the repository through the web interface, you should be able to see your commit, and the files should reflect your changes.

Best Practices
------

Here are some of my expectations/suggestions for using git version control.  As an example, [here](https://bitbucket.org/gramacylab/deepgp-ex/src/master/) is one of my repositories which demonstrates many of these tips.

* **Push your work frequently!** You don't reap the benefits of version control unless you are regularly committing/pushing your work.  Don't work more than a couple hours without pushing your work to the repo.  Your commit history should reflect the work you put in. 
* **File names:** Do NOT use spaces in any folder/file names.  Spaces make it difficult to navigates folders/files within the terminal.  Similarly, avoid using periods as these should be reserved for file extensions.  Instead, use underscores and dashes.
* **File types:** Git version control is designed for text-based files (e.g., `.R`, `.Rmd`, `.tex`, `.txt`, `.csv`, `.py`, `.sh`).  When your files are text based, git allows for easy tracking of changes and can even show you the exact differences between multiple file versions.  We are not using git for general file storage (our repositories actually have limited storage capacity).  We need to be strategic with the files that we push to the repo (this helps keep things clean and organized too).  Some specific guidelines:
  + Avoid putting other file types (e.g., `.pdf`, `.Rproj`, `.png`) on the repo unless strictly necessary.  For a PDF, push the source code that can be used to generate the file, but only build the PDF file locally.  Do the same with images and figures - push the code used to generate the figure but not the figure itself.  The exception is when figures are used inside another file (for example, when we're writing a paper it is necessary to push the images which will be included in the compiling of the paper).  
  + If at all possible, save results in `.csv` or `.txt` or `.dat` files, which are ideal for version control.  Do not use an `.Rdata` object when a `.csv` would suffice.  Similarly, do not use `.xlsx`, as git has no recourse for handling extra excel functionality.
  + Similarly, avoid pushing extraneous data files to the repo.  Files like `.Rhistory`, `.RData`, `.DS_store`, `.log` are generated locally and do not belong on the repository.  I recommend including these file extensions in a `.gitignore` file, so they are automatically ignored.
* **Documentation:** Use `README.md` files to provide relevant documentation (in the home directory but also in any "beefy" folders).  The README can include details on what scripts/files do, references, narration, notes, background information, etc.
* **Structure:** Use folders to structure and organize your repository.  Name folders appropriately and use them to your advantage.  If you have a folder with 20+ files in it, then you should be breaking things down into more folders (unless a folder is just storing results, say for 100 Monte Carlo repetitions, then it makes sense to have 100 files in the same place).

