(Companion piece to the powerpoint presentation I gave 2022-02-17, available [here](https://www.dropbox.com/sh/sbr83egmoxbelmi/AAB5dfkFYxer2-FtPW14EKXVa?dl=0))

N.B. all of the below assumes that you have git installed on your computer and linked to a github account. There's [tutorials on github](https://docs.github.com/en/get-started/quickstart/hello-world), some will vary depending on your operating system etc 


Version control tools such as git provide a simple but effective tool to record the creation, modification and deletion of plain-text objects (code, in our case)

Briefly, git allows you to track changes to these plain text files, and undo them if necessary. Github allows you to sync these changes to a remote location, so that they:
- have an external backup
- are nicely visualised in a web interface
- can be synced with
	- other machines
	- other users
- are available to the world, if you choose

For most of us, code will need to be published when we publish our papers, and github is the most widely-accepted way of doing this. In theory you could push all your code to github right when the paper is accepted, but that denies us a lot of the advantages we would have had if we'd been using it as early as possible. If you're not using it yet, today's as early as possible: welcome.

There are many ways to do all of this, for the R users among us the easiest is probably through Rstudio. There are however many other tools such as the [Github Desktop app](https://desktop.github.com), plugins for most code-editing software, and using your computer's command-line interface. Most tutorials on git and github AREN'T for Rstudio, as most programmers don't use R or Rstudio. But the terminology and principles should be the same no matter what you're using.

# creating a git repo

If we're using Rstudio there are three ways we can start working with git and github:
- Create a local git repository in a directory using a different app or in the command line. Then start an rstudio project in the tracked directory
- Create an Rstudio project and click 'create a git repository'
- Create a repository on github, and then when creating an Rstudio project choose 'version control > clone a project from a git repository'

If you're using the first two options, you will then have to create an empty repository on github, and then github will provide's instructions on how to push your local repository to it. In the ppt/video I presented, I did the final option. When you create a repository on github you can specify if it should be public or private (everyone can see, or only people you specify can see), and invite any other github users who you think should have access. If you change your mind on any of this stuff later, you can change it.

# Using the git repo

Generally a git repo should be used for a single, standalone piece of work. For us that typically means a paper, dissertation, thesis-chapter, or R package.

You'll want to start by making a `README.md` file and a `.gitignore` file: 
- The README is a good place to tell others (and yourself in 4 years when you've forgotten everything) what the repo actually **is**. 
- The .gitignore file is a list of files and directories for git to ignore. Git will happily track any files which you tell it to, but it's only meant to be used for plaintext files. Tracking non-plaintext files is mostly pointless, and tracking large files make git run **very** slowly. It can be useful to include some dummy data (for example a small csv) in your repository, but you won't want to include full datasets, and definitely not data that's in a non-plaintext format. Putting `data/raw_data/*`, `data/processed_data/*` and `figures/*` in the `.gitignore` file is a good start, that'll prevent git from tracking your raw data, processed data, and figures.

## Adding files
Git won't start tracking any files until you tell it to, by 'adding' them. In Rstudio, if our project lives in a directory that's being used as a git repository, you'll see a 'Git' tab on the top-right of your screen, alongside 'Environment', 'History' and 'Connections'. Untracked files will have a yellow question-mark symbol next to them, modified files will have a blue 'M' symbol next to them, and deleted ones have a red 'D' symbol next to them. To 'stage' a file (add it to the list of files to be commited), click the tickbox next to it and then click 'commit'. 

## Commiting files
Clicking 'commit' in the section above takes you to the 'review changes' screen, where you can add a commit message to this action. A commit is a way of creating a snapshot of your repository at the present moment, with a message attached to say what's meaningful about this particular snapshot. Always give a commit message, and always try and make them useful. "Created file x", "added boxplot" or "tidied code" are all useful commit messages, for example. 'edit' is a bad commit message.

Most of your commits will take place when you modify a script, and so they allow you a way of tracking changes as your code evolves over time. They then let you 'undo' if it turns out you want to turn back time and go back to an earlier point. In Rstudio you can 'revert' uncommited changes to a file to then have it in the same state that it was in in the previous commit ('more' and then 'revert' in the Git pane). Or you can leave Rstudio and use `git checkout` to go back to a previous commit, using a [tutorial like this one](https://medium.com/swlh/using-git-how-to-go-back-to-a-previous-commit-8579ccc8180f).

# Interacting with Github

Your interactions with github will mostly be 'pushing' commits from your computer onto github, and perhaps 'pulling' them from github to your computer. These ideas should hopefully be fairly self-explanatory (push things away from you, pull them towards you from far away), and have nice big buttons in Rstudio to click for them. If you're working on multiple machines, or multiple people are working on the same repo, it's best to be in the habit of clicking 'pull' before every 'push', to reduce the chance of sending changes to github which conflict with the code thats already on github.

# Collaborating

## Basics:
Now that your code is on github, it should be ready to collaborate on! If the repository is public, anyone can see it with the url. You can invite other users to the repository (whether it's public or private) by opening the repository on github, then clicking settings / collaborators. At its most basic, this is all you need for collaborating and reviewing code, as your collaborators can see and edit the code. But there are some features which make this easier

## Branches and official code-review
Branches sound far more confusing than they actually are, and a lot of their documentation is a bit opaque as they're designed for software development etc, but they're also a useful concept for us. In software development it can be useful to have multiple versions of a repository: typically there is a 'main' branch, which is where the code which definitely works lives. And then there can be multiple alternate branches where development takes place, without the risk of destroying the main app/pipeline/whatever. Once the code in a development branch is felt to be sound, it can then be 'pulled' into the 'main' branch where the good code lives.

This is useful for us for two reasons: firstly, by using branches we give ourselves the ability to write new code that might be crap, and not have it messing up our established code. Secondly, we can assign 'reviewers' on github when we choose to pull code from one branch into another; in our case, pulling code from a development branch into the 'main' one where the good code lives.

You can make a new branch easily in Rstudio, using the 'New Branch' button in the Git pane. Then, using this branch, you can write code as normal, commiting the changes as normal. But when you want to put that new code into the 'main' branch where the good code lives, you go onto the repository on github and create a 'pull request': a request to pull the code from one branch into another. At this point you can assign reviewers to the pull request and they can go in and comment on the individual changes: suggesting improvements, giving feedback (positive and negative) and approving/rejecting the changes before they are then merged into the main branch. In this way we can regularly evaluate one another's code for understandability and whether or not it actually works. This makes it much easier to set up systems of reviewing one anothers code little and often, rather than the usual scientific system where we finish a large piece of code and hope nobody ever looks at it.






# Some useful references
- A lot of the above was inspired by a tutorial Our Coding Club gave at Oxford in the before times, they have a bit of a walkthrough available [here](https://ourcodingclub.github.io/tutorials/git/index.html).
- The idea of setting up a within-lab system of code review was inspired by Dave attending a workshop on code review, whose slides are available [here](https://speakerdeck.com/leriomaggio/code-review-workshop-for-researchers-ssi-2022-closing-remarks). As they mention (and I forgot to say in my presentation), some of the presenters in that workshop actually run [the Oxford code review network](https://github.com/OxfordCodeReviewNet/forum), though it isn't yet very active. It would be cool to interact with them more in the future, but I assume that something small and within-lab may be slightly less intimidating to some of us at first, and I suspect that they'll have limited familiarity with R.
- When your code is one day finished and the paper accepted, you'll want to create a permanent, archived version of it with a citable DOI. One of the easiest ways to do this is [archiving it with Zenodo](https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content)
- I referenced Micah Allen's tweet in the powerpoint, [his thread on organising your analyses etc](https://twitter.com/micahgallen/status/1001362580710088704?s=20&t=kAMXkPqePQGI3RoI_qL1dA) is short but good. I think he's confused that he went viral with a tweet about directory structures, but nerds gonna nerd.
