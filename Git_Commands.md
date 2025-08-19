# Git and Github cheet sheet:
## In a nutshell, Git is a version control for project.
So we can use a distribuyed version control system: Each system has a full version of the project on it in which one of them can be the main servers
* Git let's you to save the changes of the each version of the project not the hole version.(by using a snapshot of each version)
* Git can be local version control system on your own pc --> But GitHub is the server for this control.
* How does Git WORKS??? 
1. Working Directory:\
The Working Directory is the physical folder on your computer where you can see all your project files. It's the place where you do all your work: you write code, add new files, and 	modify existing ones. When you make changes here, Git sees them as "untracked" or "modified." These changes are not yet part of your project's version history.
---------------------------
2. Staging Area:\
Also known as the "Index," the Staging Area is a temporary layer that sits between your Working Directory and the Git Repository. When you run the git add command, you're taking 		specific changes from your Working Directory and placing them in the Staging Area. This lets you prepare a snapshot of your changes before committing them. It's a key feature that allows you to group related changes together into a single, meaningful commit, even if you have other unrelated changes in your working folder.
---------------------------
3. .git Directory (Repository): \
The Git Repository is the core of your project. It's a hidden folder named .git that stores all of your project's history, including all the commits, branches, and tags. When you use the git commit command, Git takes everything you've placed in the Staging Area and permanently saves it as a new, permanent version of your project inside the repository. Each commit is like a permanent snapshot in time, and you can always go back to it.
---------------------------
## vs code 
in terminal visual studio code can open by using:
```bash
$ code
```
```bash
‍‍‍‍‍‍‍‍$ code ~/project directory/eg. main.py
```
or 
```bash
$ cd ~/project directory --> code . 
``` 
which opens code in current directory

## Setting Your Default Text Editor:

if you want vscode to be your main editor in git you can simply use:
```bash
$ git config --global core.editor "code --wait"
```
---------------------------
## Git Configs:
 Git configuration is done using git config and settings are stored in three levels:
 - System (--system): `/etc/gitconfig` – applies to all users and repositories.
 - Global (--global): `~/.gitconfig` or `~/.config/git/config` – specific to your user.
 - Local: `.git/config` in the repo – specific to that repository.
Each level overrides the previous one.
 
### Set your name and email (required for commits):
```bash
 $ git config --global user.name "John Doe"
 $ git config --global user.email "john@example.com"
```
### check settings:
```bash
 $ git config --list
```
### To see where a setting is defined: 
``` 
 $ git config --show-origin --get-regexp user.name
```
## Git Basics
### Getting a Git Repository
You can set up a Git repository in two ways:
#### 1. Initialize a New Repository
Go to your project directory and run:
```bash
$ git init
```
This creates a .git subdirectory containing all repository metadata. No files are tracked yet.
To start tracking files and make the first commit:
```bash
$ git add <file>          # Track specific file
$ git add *.c             # Add all .c files
$ git add LICENSE         # Add LICENSE file
$ git commit -m "Initial commit"
```
#### 2. Clone an Existing Repository
To copy a remote Git repository:
```bash
git clone https://github.com/libgit2/libgit2
```
This:
* Creates a local directory named libgit2
* Initializes .git
* Downloads all project history
* Checks out the latest version
To clone into a custom directory name:
```bash
$ git clone https://github.com/libgit2/libgit2 mylibgit
```
Supported Protocols:
* HTTPS: https://github.com/user/repo.git
* SSH: user@server:path/to/repo.git or ssh://user@server/path
* Git: git://server/path/to/repo.git

### Recording Changes in the Repository
Once you have a repo, you’ll work in three main areas:
* Working Directory: Your actual files.
* Staging Area (Index): Files marked for next commit.
* Repository: Committed snapshots.
Files can be:
* Tracked: Already in the
repo (unmodified, modified, or staged).
* Untracked: Not in the last commit and not staged.
#### Check File Status
Use:
```bash
$ git status
```
Example output:
```bash
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
```
After adding a new file:
```bash
Untracked files:
  README
```
Use short status format:
```bash
$ git status -s
```
Output meaning:
| SYMBOL | MEANING         |
|--------|------------------|
| ??     | Untracked file   |
| A      | New file staged  |
| M      | Modified file    |
| D      | Deleted file     |
| R      | Renamed file     |

#### Tracking New Files
Stage a new (untracked) file:
```bash
$ git add README
```
Now it appears under:
```bash
Changes to be committed:
  new file: README
```
#### Staging Modified Files
If a tracked file (e.g., CONTRIBUTING.md) is edited:
```bash
$ git status
```
Shows:
```bash
Changes not staged for commit:
  modified: CONTRIBUTING.md
```
Stage it:
```bash
$ git add CONTRIBUTING.md
```
#### Ignoring Files with .gitignore
Create a .gitignore file to exclude unwanted files (logs, binaries, temp files, passwords(.env),...).
Example:
```bash
*.log           # Ignore all .log files
*.o             # Object files
*.a             # Archive files
*~              # Editor backup files (e.g., Emacs)
build/          # Entire build directory
/TODO           # Only root-level TODO
doc/*.txt       # Only .txt in doc/ (not subdirs)
doc/**/*.pdf    # All .pdf files in doc/ and subdirectories
!important.log  # Track this even if it matches a rule
```
Rules:
* Blank lines or lines starting with # are ignored.
* Use * (any chars), ? (single char), [abc] (char class).
* Use /** / for recursive matching (e.g., a/**/z matches a/b/c/z).
* Start with / to match root only.
* End with / to match directories only.
* Use ! to negate a pattern.
###  Viewing Changes
Use git diff to see exact changes, not just filenames.

#### Compare Working Directory vs Staging Area
```bash
$ git diff
```
Shows unstaged changes (what you've edited bun not "git add" ed).

#### Compare Staged Changes vs Last Commit
```bash
$ git diff --staged
```
or
```bash
$ git diff --cached
```
Shows what will be included in the next commit.
### Committing Changes
Once files are staged:
```bash
$ git commit
```
This opens your default editor (set via git config --global core.editor) to write a message.

The editor shows:

* Commented git status output
* Lines starting with # are ignored
* An empty message cancels the commit
Or, commit with a message inline:
```bash
$ git commit -m "Fix login bug"
```
Output example:
```bash
[master 463dc4f] Fix login bug
 2 files changed, 5 insertions(+)
 create mode 100644 README
```
### Skip the Staging Area
To stage and commit all tracked and modified files at once:
```bash
$ git commit -a -m "Commit message"
```
This is equivalent to:
```bash
$ git add <all tracked files>
$ git commit -m "Commit message"
```
### Removing Files
To remove a file from Git and disk:
```bash
$ git rm filename
```
Then commit:
``` bash
$ git commit -m "Remove old cinfig"
```
If the file is modified/uncommitted, use -f:
```bash
$ git rm -f filename 
```
To keep the file on disk but stop tracking it:
```bash
$ git rm --cached filename
```
Useful for accidentally added files(e.g. logs, binaries)

#### Remove Multiple Files
Use wildcards (escape * to prevent shell expansion):
```bash
$ git rm log/\*.log     # All .log files in log/
$ git rm \*~            # All files ending in ~
```
### Moving (Renaming) Files
Git doesn't track moves, but detects them.
#### Rename file 
```bash
$ git mv old.txt new.txt
```
After this, git status shows:
```
renamed: old.txt -> new.txt
```
This equivalent to:
```bash
$ mv old.txt new.txt
$ git rm old.txt
$ git add new.txt
```
