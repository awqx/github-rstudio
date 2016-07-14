# github-rstudio
How to (to the best of my knowledge) properly get GitHub and RStudio to work together

This is not code, sorry, just text.

---HOW GITHUB WORKS---
Every GitHub repository starts with a master branch. This branch is decisive copy of a project, and edits to the master branch should be done very cautiously. Instead of every team member working directly on the master branch (which would probably cause something to break irreparably), preliminary edits should be made on a new branch . When the new-branch is done, a pull request can be made. When the pull request is approved by the owner of the project, edits from the new branch will be merged into the master branch. The new-branch can then be deleted. 

There's a bit more to it, but that's the basic idea. 
