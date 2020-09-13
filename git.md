# git

### make a new repository

`git init`

- Make a "New Repository" on github.com, and copy and paste the `git remote add origin` line into your terminal to link your local repository with the one online 

### save your code

`git add .`

`git commit -m "my message"`

`git push origin master`

### note

The `.gitignore` file lets you add specific files and folders that you dont want saved on github. Always add the `/node_modules` folder!!!

### copy a repo

`git clone {url.git}`: copy an entire repository to your local computer. Then you can `cd` into it, and run `npm install` to install all the dependencies.

# git branches

### branch stuff
See what branch you are current on:
`git branch`

Switch branches:
`git checkout branch-name`

See your local changes
`git status`

There is always a default branch called "master"

### create a branch

`git checkout -b BRANCH_NAME`
- (the -b is what creates a new branch)
- for example: "git check -b my-new-feature"
- then you can push it to github
- `git add .`
- `git commit -m "message"`
- `git push origin my-new-feature`
- and then on github.com, you can open a "pull request" and somebody else can review your code.

### merging

If the master branch has been changed by somebody else, you need to pull before you can push.

Commit to a repository that has many contributors:

- You are in your own branch
- `git pull origin master`
- This will pull any updates since last time you pulled
- `git merge master`
- This will merge any changes from the master branch into your local branch, *so you can resolve conflicts if there are any.*
- If there are conflicts, you need to *add* and *commit* again.
- `git push origin my-new-feature`
- Finally, the new branch is created on github.com

