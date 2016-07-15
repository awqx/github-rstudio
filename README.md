# GitHub and RStudio
How to (to the best of my knowledge) properly get GitHub and RStudio to work together

##How GitHub Works

Every GitHub repository starts with a master branch. This branch is decisive copy of a project, and edits to the master branch should be done very cautiously. Instead of every team member working directly on the master branch (which would probably cause something to break irreparably), preliminary edits should be made on a new branch . When the new-branch is done, a pull request can be made. When the pull request is approved by the owner of the project, edits from the new branch will be merged into the master branch. The new-branch can then be deleted. 

There's a bit more to it, but that's the basic idea. 


##RStudio and GitHub

###Going from RStudio to GitHub

Make sure Git is installed before continuing. And also make a GitHub account.

In RStudio, select Tools --> Version Control --> Git 

Tools --> Global Options --> Git/SVN

Confirm the path to the Git executable is correct

Select Create RSA key...

Close the resulting window

Select View public key, and copy the key

Go to your GitHub account, and open settings --> SSH keys --> Add SSH key --> Paste the copied public key

Back to Rstudio --> Tools --> Shell

  Type:
  
  git config --global user.email "example@example.com"
  
  git config --global user.name "exampleuser"
  
  Use your GitHub username

In RStudio, create a New Project --> New Directory

Name the project, and select "Create a git repository"

Make a new script, as normal. 

Saving the script results in it showing up in the Git tab in the panel that includes the Environment & History tab

Click the right file, and the status should turn to a green "A"

Commit the file, and write a comment in Commit message

The file is committed in the computer/server's repository, but not on GitHub

The file should be pushed to a GitHub repository

Create a new repository, or select the one you want

Back to RStudio Tools --> Shell

  Type:

  git remote add origin https://github.com/exampleuser/examplerepository.git

  git config remote.origin.url git@github.com:exampleuser/examplerepository.git

  git pull -u origin master

  git push -u origin master

The file should be in GitHub, and the pull/push buttons in RStudio will now work



--GitHub to RStudio--

In RStudio: New Project --> Version Control --> Clone Git Repository

Enter the repository URL

Tools --> Shell

  Type:

  git config remote.origin.url

  git@github.com:exampleuser/examplerepository.git
