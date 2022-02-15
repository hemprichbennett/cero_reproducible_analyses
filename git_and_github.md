N.B. all of the below assumes that you have git installed on your computer and linked to a github account. There's [tutorials on github](https://docs.github.com/en/get-started/quickstart/hello-world), some will vary depending on your operating system etc 


Version control tools such as git provide a simple but effective tool to record the creation, modification and deletion of plain-text objects (code, in our case)

Briefly, git allows you to track changes to these plain text files, and undo them if necessary. Github allows you to sync these changes to a remote location, so that they:
- have an external backup
- are nicely visualised in a web interface
- can be synced with
	- other machines
	- other users

There are many ways to do this, for the R users among us the easiest is probably through Rstudio. There are however many other ways such as the Github Desktop app, most code-editing software, and your computer's command-line interface. Most tutorials AREN'T for Rstudio, as most programmers don't use R or Rstudio. But the terminology and principles are the same.

# creating a git repo

If we're using Rstudio there are three ways we can start working with git:
- Create a local git repository in a directory using a different app or in the command line. Then start an rstudio project in the tracked directory
- Create an Rstudio project and click 'create a git repository'
- Create a repository on github, and then when creating an Rstudio project choose 'version control > clone a project from a git repository'

If you're using the first two options, you will then have to create an empty repository on github, and then follow github's instructions on how to push your local repository to it.

# Using the git repo

Generally a git repo should be used for a single, standalone piece of work. For us that typically means a paper, dissertation, thesis-chapter, or R package.

You'll want to start by making a `README.md` file and a `.gitignore` file: 
- The README is a good place to tell others (and yourself in 4 years when you've forgotten everything) what the repo actually **is**. 
- The .gitignore file is a list of files and directories for git to ignore. Git will happily track any files which you tell it to, but it's only meant to be used for plaintext files. Tracking non-plaintext files is mostly pointless, and tracking large files make git run **very** slowly. It can be useful to include some dummy data (for example a small csv) in your repository, but you won't want to include full datasets, and definitely not data that's in a non-plaintext format. Putting `data/raw_data/*`, `data/processed_data/*` and `figures/*` in the `.gitignore` file is a good start, that'll prevent git from tracking your raw data, processed data, and figures.

## adding files
Git won't start tracking any files until you tell it to, by 'adding' them. In Rstudio if our project is in a directory that's being used as a git repository, you'll see a 'Git' tab on the top-right of your screen, alongside 'Environment', 'History' and 'Connections'. Untracked files will have a yellow question-mark symbol next to them, modified files will have a blue 'M' symbol next to them, and deleted ones have a red 'D' symbol next to them. To add a file, click the tickbox next to it and then click 'commit'. 

## commiting files
This takes you to the 'review changes' screen, where you can add a commit message to this action. A commit is a way of creating a snapshot of your repository at the present moment, with a message attached to say what's meaningful about this particular snapshot. Always give a commit message, and always try and make them useful. "Created file x", "added boxplot" or "tidied code" are all useful commit messages, for example