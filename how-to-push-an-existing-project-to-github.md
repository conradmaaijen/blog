How to Push an Existing Project to Github

From your terminal, run the following commands after navigating to the folder you would like to add.

## Initialize the Git Repo

Make sure you are in the root directory of the project you want to push to GitHub and run: 
*Note: If you already have an initialized Git repository, you can skip this command.*

---

![How to Push an Existing Project to Github](/images/github.jpeg)

	git init

This step creates a hidden `.git` directory in your project folder, which the `git` software recognizes and uses to store all the metadata and version history for the project.

## Add the files to Git index

	git add -A

The `git add` command is used to tell git which files to include in a commit, and the `-A` (or `--all`) argument means “include all”.

## Commit Added Files

	git commit -m 'Added my project'

The `git commit` command creates a new commit with all files that have been “added”. The `-m` (or `--message`) sets the message that will be included alongside the commit, used for future reference to understand the commit. In this case, the message is: `'Added my project'`.

## Add a new remote origin

	git remote add origin git@github.com:sammy/my-new-project.git

*Note: Remember, you will need to replace the highlighted parts of the username and repo name with your own username and repo name.*

In git, a “remote” refers to a remote version of the same repository, which is typically on a server somewhere (in this case, GitHub). “origin” is the default name git gives to a remote server (you can have multiple remotes) so git `remote add origin` is instructing git to add the URL of the default remote server for this repo.

## Push to GitHub

	git push -u -f origin main

The `-u` (or `--set-upstream`) flag sets the remote `origin` as the upstream reference. This allows you to later perform `git push` and `git pull` commands without having to specify an `origin` since we always want GitHub in this case.

The `-f` (or `--force`) flag stands for force. This will automatically overwrite everything in the remote directory. We’re using it here to overwrite the default README that GitHub automatically initialized.

*Note: If you did not include the default README when creating the project on GitHub, the -f flag isn’t really necessary.*

## All together

	git init
	git add -A
	git commit -m 'Added my project'
	git remote add origin git@github.com:sammy/my-new-project.git
	git push -u -f origin main



Tags: git, github
