N.B. all of the below assumes that you have git installed on your computer and linked to a github account. There's [tutorials on github](https://docs.github.com/en/get-started/quickstart/hello-world), some will vary depending on your operating system etc 


Version control tools such as git provide a simple but effective tool to record the creation, modification and deletion of plain-text objects (code, in our case)

Briefly, git allows you to track changes to these plain text files, and undo them if necessary. Github allows you to sync these changes to a remote location, so that they:
- have an external backup
- are nicely visualised in a web interface
- can be synced with
	- other machines
	- other users

There are many ways to do this, for the R users among us the easiest is probably through Rstudio. There are however many other ways such as the [Github Desktop app](https://desktop.github.com), most code-editing software, and your computer's command-line interface. Most tutorials AREN'T for Rstudio, as most programmers don't use R or Rstudio. But the terminology and principles are the same.

# creating a git repo

If we're using Rstudio there are three ways we can start working with git and github:
- Create a local git repository in a directory using a different app or in the command line. Then start an rstudio project in the tracked directory
- Create an Rstudio project and click 'create a git repository'
- Create a repository on github, and then when creating an Rstudio project choose 'version control > clone a project from a git repository'

If you're using the first two options, you will then have to create an empty repository on github, and then follow github's instructions on how to push your local repository to it.

# Using the git repo

Generally a git repo should be used for a single, standalone piece of work. For us that typically means a paper, dissertation, thesis-chapter, or R package.

You'll want to start by making a `README.md` file and a `.gitignore` file: 
- The README is a good place to tell others (and yourself in 4 years when you've forgotten everything) what the repo actually **is**. 
- The .gitignore file is a list of files and directories for git to ignore. Git will happily track any files which you tell it to, but it's only meant to be used for plaintext files. Tracking non-plaintext files is mostly pointless, and tracking large files make git run **very** slowly. It can be useful to include some dummy data (for example a small csv) in your repository, but you won't want to include full datasets, and definitely not data that's in a non-plaintext format. Putting `data/raw_data/*`, `data/processed_data/*` and `figures/*` in the `.gitignore` file is a good start, that'll prevent git from tracking your raw data, processed data, and figures.

## Adding files
Git won't start tracking any files until you tell it to, by 'adding' them. In Rstudio if our project is in a directory that's being used as a git repository, you'll see a 'Git' tab on the top-right of your screen, alongside 'Environment', 'History' and 'Connections'. Untracked files will have a yellow question-mark symbol next to them, modified files will have a blue 'M' symbol next to them, and deleted ones have a red 'D' symbol next to them. To add a file, click the tickbox next to it and then click 'commit'. 

## Commiting files
Clicking 'commit' in the section above takes you to the 'review changes' screen, where you can add a commit message to this action. A commit is a way of creating a snapshot of your repository at the present moment, with a message attached to say what's meaningful about this particular snapshot. Always give a commit message, and always try and make them useful. "Created file x", "added boxplot" or "tidied code" are all useful commit messages, for example. 

Most of your commits will take place when you modify a script, and so they allow you a way of tracking changes as your code evolves over time. They then let you 'undo' if it turns out you want to turn back time and go back to an earlier point. In Rstudio can 'revert' uncommited changes to a file to the have it in the same state that it was in in the previous commit ('more' and then 'revert' in the Git pane). Or you can leave Rstudio and use `git checkout` to go back to a previous commit, using a [tutorial like this one](https://medium.com/swlh/using-git-how-to-go-back-to-a-previous-commit-8579ccc8180f).

# Interacting with Github

Your interactions with github will mostly be 'pushing' commits from your machine, and 'pulling' them from github. These should hopefully be fairly self-explanatory, and have nice big buttons in Rstudio to click for them. If you're working on multiple machines, or multiple people are working on the same repo, it's best to be in the habit of clicking 'pull' before 'push', to reduce the chance of sending changes which conflict with the code thats on github.

# Collaborating

## Basics:
Now that your code is on github, it should be ready to collaborate on! If the repository is public, anyone can see it with the url. You can invite other users to the repository (whether it's public or private) by opening the repository on github, then clicking settings / collaborators. 

## 






# And finally (archiving forever)



# Some useful references
- When your code is one day finished and the paper accepted, you'll want to create a permanent, archived version of it with a citable DOI. One of the easiest ways to do this is [archiving it with Zenodo](https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content)