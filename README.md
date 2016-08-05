# GitHub and RStudio
How to (to the best of my knowledge) properly get GitHub and RStudio to work together. Credit to http://www.r-bloggers.com/rstudio-and-github/ and stackoverflow.com as well as http://www.enoriver.net/2014/10/12/recipe-for-pairing-up-rstudio-with-github/.


##Github - The Most Basic Info
Every GitHub repository starts with a master branch. This branch is decisive copy of a project, and edits to the master branch should be done very cautiously. Instead of every team member working directly on the master branch (which would probably cause something to break irreparably), preliminary edits should be made on a new branch . When the new-branch is done, a pull request can be made. When the pull request is approved by the owner of the project, edits from the new branch will be merged into the master branch. The new-branch can then be deleted. 

##RStudio and GitHub

###RStudio to GitHub

Make sure Git is installed before continuing. And also make a GitHub account.
Examples will be surrounded by [brackets]. Assume anything not surrounded by brackets should be typed verbatim.

- In RStudio, select Tools --> Version Control --> Git
- Tools --> Global Options --> Git/SVN
- Confirm the path to the Git executable is correct
- Select "Create RSA key..."
- Close the resulting window
- Select View public key, and copy the key
- Go to your GitHub account, and open settings --> SSH keys --> Add SSH key --> Paste the copied public key
- Back to Rstudio --> Tools --> Shell
  - Type:
  - git config --global user.email "[example]@[example].com"
  - git config --global user.name "[exampleuser]"
    - Use your GitHub username
- In RStudio, create a New Project --> New Directory
- Name the project, and select "Create a git repository"
- Make a new script
- Saving the script results in it showing up in the Git tab in the panel that includes the Environment & History tab
- Click the file, and the status should turn to a green "A"
  - Future modifications of the file will show as a blue "M" standing for "Modified"
- Commit the file, and write a comment in Commit message
  - The file is committed in the computer/server's repository, but not on GitHub
- The file needs to be pushed to a GitHub repository
- Create a new repository, or select the one you want

- Back to RStudio Tools --> Shell
  - Type:
  - git remote add origin https://github.com/[exampleuser]/[examplerepository].git
  - git config remote.origin.url git@github.com:[exampleuser]/[examplerepository].git
  - git pull -u origin master
  - git push -u origin master
    -If this doesn't work, and the error says something about "unrelated histories", use git pull --allow-unrelated-histories 
- The file should be in GitHub, and the pull/push buttons in RStudio will now work
- Sometimes the past few steps don't work, which is a pain, so let's try another recommendation
- Go back to GitHub, and remove the repository (if the past steps didn't work, there should be nothing there and nothing will be lost by deleting the repository)
- Re-create the repository, and make sure you DON'T initialize it with a README.md
- Options should show something that gives you options, one of which will be "...or push an existing repository from the command line..."
- This is the thing you want
- GitHub will helpfully provide something that looks like "git@github.com:[user]/[repository].git" 
  - Copy it to the clipboard now to save a little trouble later
- Go back to RStudio and open the Shell 
  - Type:
  - git remote add origin git@github.com:[user]/[repository].git
  - git pull -u origin master
  - git push -u origin master

####Pushing and Pulling
- At this point, the Push/Pull buttons in the Git tab of RStudio should work. 
- First, pull from GitHub to make sure everything is up-to-date. 
- In order to push, you have to make a commit first (see above), and then press the push button. 
  - If pushing doesn't work with the buttons, try going to the Git shell and using the command:
  - git push origin [example-branch]
  - (of course, replace "example-branch" with the branch you're pushing to.)

###GitHub to RStudio
- In RStudio: New Project --> Version Control --> Clone Git Repository
- Enter the repository URL
- Tools --> Shell
  - Type:
  - git config remote.origin.url git@github.com:exampleuser/examplerepository.git
  
##Some Other Notes
- Git can be unnecessarily aggressive. When a command doesn't work, it'll say something like "fatal" in red letters. This is Git's equivalent of an error message; don't be alarmed into thinking something permanently broke
