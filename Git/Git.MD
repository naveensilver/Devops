# Git

* Git (Global Information Tracker) is a version control system (VCS) and source code management (SCM) tool.

* Git is platform-independent, free and open-source, and efficient for large projects.

## History of Version Control Systems (VCS)

1. **SCCM (1972)**: Single file, single user.
2. **RCS**: Multiple files, single user.
3. **CVS**: Multiple files and directories, single user.
4. **SVN (2000)**: Multiple files and directories, multiple users.
5. **GIT (2005)**: Multiple files, directories, and multiple users due to Distributed Version Control System (DVCS).

## Distributed Version Control System (DVCS)

* Allows multiple users to collaborate and merge changes into a repository.

* Provides backup copies, fast merging, flexible branching, rapid feedback, and offline work capability.

## Why Git?

* Facilitates version rollback, collaboration, and efficient project management.

## Git Stages

1. **Working Directory**: Initial stage with untracked files.
2. **Staging Area**: Files are tracked and prepared for commit.
3. **Repository**: Contains all committed files and history.

## Types of Repositories

1. **Local Repo**: Stored on the local system.
2. **Remote Repo**: Stored on a remote server (e.g., GitHub).
3. **Central Repo**: Main repository on GitHub.

## Installation and Initial Setup

1. **Install Git**: `yum install git -y`
2. **Initialize Repository**: `git init .`
3. **Check Version**: `git --version`
4. **Configure User**:
    ```sh
    git config --global user.name "your_name"
    git config --global user.email "your_email"
    ```

## Basic Git Commands

* **Create File**: `touch filename`
* **Track File**: `git add filename` / `git add *` / `git add .`
* **Check Status**: `git status`
* **Commit Changes**: `git commit -m "message" <filename/*/.>`
* **Untrack File**: `git rm --cached filename`
* **View Logs**: `git log` / `git log -2` / `git log --oneline`

## Branch Management

* **List Branches**: `git branch`
* **Create Branch**: `git branch branch-name`
* **Rename Branch**: `git branch -m old-name new-name`
* **Switch Branch**: `git checkout branch-name`
* **Create & Switch Branch**: `git checkout -b branch-name`
* **Delete Branch**: `git branch -d branch-name`

## Merging and Conflict Resolution

* **Merge Branch**: `git merge branch-name`
* **Resolve Conflicts**: Edit files, then `git add` and `git commit`

## Stashing

* **Create Stash**: `git stash`
* **Apply Stash**: `git stash apply`
* **List Stashes**: `git stash list`
* **Delete Stash**: `git stash pop` / `git stash clear`

## Reverting and Resetting

* **Revert Commit**: `git revert commit-id`
* **Reset Commit**: `git reset commit-id`

## Git Ignore

* **Create .gitignore**: Add patterns to ignore files (e.g., `*.txt`).

## GitHub Integration

1. **Push to GitHub**:
    ```sh
    git remote add origin <GitHub URL>
    git push -u origin branch-name
    ```
2. **Clone Repository**: `git clone <Repo URL>`
3. **Fetch and Merge**: `git fetch && git merge` or `git pull`
4. **Fork Repository**: Use GitHub interface to fork and clone.

## Tagging

* **Create Tag**: `git tag tag-name`
* **View Tags**: `git tag`
* **Push Tag**: `git push origin tag-name`
* **Delete Tag**: `git tag -d tag-name`

## Additional GitHub Commands

* **Check Commit History**: `git log origin/master`
* **Show Remote Branches**: `git remote show origin`
* **Delete Remote Branch**: `git push --delete origin branch-name`

