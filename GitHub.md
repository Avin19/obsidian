#Github

## 1. Set Up GitHub
-  <b> Create a GitHub account: </b> Sign up at GitHub.
- <b> Install Git : </b> Download and install Git on your machine from Git's Website.
- <b> Configure Git : </b> Set up your name and email, which will be linked to your GitHub account. Use these Commands:
```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

## 2. Creating a Repository 
- <b> New Repository : </b> In GitHub, click on the "+" icon, choose "New Repository," name your project, and select visibility (public or private).
- <b> Initialize Repository : </b> You can add a README.md,  .gitignore ( to ignore unnecessary files), or license if needed.

## 3. Using Git Commands in GitHub
- <b> Clone a Repository: </b> Clones an existing repository to your local machine:
``` bash
git clone https://github.com/username/repository-name.git
```
- <b> Making Changes: </b> After modifying files, check the status of files:
```bash
git status
```
- <b> Staging Changes : </b> Stage files before committing: 
``` bash
	git add filename # For specific file
	git add . # For all files
```
- <b> Commit Changes : </b> Save the changes with a message:
```bash
git commit -m " your descriptive message here"
```
- <b> Push to GitHub : </b> Upload local commits to GitHub : 
``` bash
git push origin main # Replace 'main' if your branch  is named differently
```
## 4. Branching and Merging 

- <b> Create a Branch : </b> Branches help you work on features independently without affecting the main code. 
```bash
git branch feature-branch-name
git checkout feature-branch-main
```
- <b> Merging Branches : </b> Merge a feature branch back into the main branch.
```bash 
git checkout main 
git merge feature-branch-main 
```
- <b> Delete a Branch </b> After merging , delete unnecessary branches.
```bash
git branch -d feature-branch-main
```
## 5. Pull Requests (PRs)
-  <b> Create a Pull Request: </b> Once you push your feature branch to GitHub, you can open a pull request to propose merging changes into the main branch.
- <b> Review and Approves PRs </b> if working in a team . others can review, comment, and approve your pull request before merging. 
## 6. Best Practices for GitHub
- <b> Use Meaningful Commit Message </b>:  Describe what the commit does, e.g., `"Fix bug in user login"`.
-  <b> Commit Often  ,  but Small :</b> Commit small, logical changes  frequently to make tracking easier.
- <b> Branch for each Feature: </b> Create separate branches from new features or bug fixes to avoid conflicts.
- <b> Keep Main Branch Stable : </b> Only merge tested, stable code into the main branch. 
- <b> Use .gitignore : </b> Exclude unnecessary files ( e.g., logs, complied files) from being tracked. 
- <b> Review Pull Requests : </b> Regular code reviews help maintain code quality and share knowledge among team members.
## 7. Collaborating with Others
- <b> Forking and Cloning : </b> For collaborative projects, fork the repository to create a copy under your GitHub account and clone it to work locally.
- <b>  Syncing Forks </b> : Regularly update your fork to stay in sync with the main project. 
  
  
  

# GIT SETUP 
#GITSETUP

Configuring user information used across all local repositories
```bash
git config --global user.name "[firstname lastname]"
```
set  a name that is identifiable for credit when review version history

```bash 
git config --global user.email "[valid-email]"
```
set an email address that will be associated with each history marker 
```bash 
git config --global color.ui auto 
```
set automatic command line coloring for Git for easy reviewing 


# SETUP & INIT

Configuring user information used across all local repositories
```bash
git init
```
Initialize an existing directory as a Git repository
```bash
git clone [url]
```
retrieve an entire repository from a hosted location via URL


# INSPECT & COMPARE

Examining logs, diffs and object information

```bash 
git log
```
show the commit history for the currently active branch

```bash 
git log branchB .. branchA
```
show the commits on branchA that are not on branchB

```bash 
git log --folow [file]
```
show the commits that changed file, even  across renames
```bash
git diff branchB ..branchA
```
show the diff of what is in branchA that is not in branchB

```bash
git show [SHA]
```
show any object in Git in Human-readable format

# TRACKING PATH CHANGES

Versioning file removes and path changes

```bash
git rm [file]
```
delete the file from project and stage the removal for commit 
```bash
git mv [existing-path] [new-path]
```
change an existing file path and stage the move
```bash
git log --stat -M
```
show all commit logs with indication of any paths that moved. 

# IGNORING PATTERNS

Preventing unintentional staging or commiting of files

```bash
logs/
*.notes
pattern*/
```
save a file with desired patterns as .gitignore with  either direct string matches or wildcard globs.

```bash 
git congig --global core.excludesfile [file]
```
system wide ignore pattern for all local repositories

# STAGE & SNAPSHOT

Working with snapshots and the Git staging area

```bash
git status
```
show modified files in working directory, staged for your next commit
```bash
git add [file]
```
add a file as it looks now to your next commit (stage)
```bash
git reset [file]
```
unstage a file while retaining the changes in working directory
```bash
git diff
```
diff of what is changed but not staged
```bash
git diff --staged
```
diff of what is staged but not yet committed
```bash
git commit -m "[decriptive message]"
```
commit your stagged content as a new commit snapshot


# BRANCH & MERGE

Isolating work in branches, changing context, and integrating changes

```bash
git branch
```
list your branches a * will appear next to the currently active branch
```bash
git branch [branch-name]
```
create a new branch at the current commit
```bash
git checkout
```
switch to another branch and check it out into your working directory 
```bash
git merge [branch]
```
merge the specified branch's history into  the current one
```bash
git log
```
show all commits in the current branch's history

# SHARE & UPDATE

Retrieving updates from another repository and updating local repos

``` bash
git remote add [alias] [url]
```
add a git URL as an alias
```bash
git fetch [alias]
```
fetch down all the branches from that Git remote
```bash
git merge [alias]/[branch]
```
merge a remote branch into your current branch to bring it up to date
```bash
git push [alias] [branch]
```
Transmit local branch commits to the remote repository branch
```bash
git pull
```
fetch and merge any commits from  the tracking remote branch

# REWRITE HISTORY

Rewriting branches, updating commits and cleaning history
```bash
git rebase [branch]
```
apply any commits of current branch ahead of specified one
```bash
git reset --hard [commit]
```
clear staging area, rewrite working tree from specified commit

# TEMPORARY COMMITS

Temporarily store modified, tracked files in order to change branches

```bash
git stash
```
save modified and staged changes
```bash
git stash list
```
list stack-order of stashed file changes
```bash
git stash pop
```
write working from top of stash stack
```bash
git stash drop
```
discard the changes from top of stash stack




