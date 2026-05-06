Git is a **version** control system used to track changes in your files. Unlike older systems, Git is **distributed**, meaning every developer has a full copy of the project history.

## Terminal Basics

Before using Git, you must know how to navigate your computer via the terminal.

- `mkdir`: Create a new folder (directory).
- `ls`: List files and folders in the current directory.
- `pwd`: "Print Working Directory" shows your current folder path.
- `cd ..\..`: Go up two directory levels.

## Setup

1. Install Git from [https://git-scm.com](https://git-scm.com/) and verify the installation in the terminal with `git version`.
2. Create a GitHub account (for remote work).
3. Configure Git and set your email and username.
4. Set an editor for commit messages (Vim is the default editor).

|Purpose|Command|
|---|---|
|Check Git version|`git version`|
|Clone a repository|`git clone <url>`|
|Set username|`git config --global user.name "Name"`|
|Set email|`git config --global user.email "mail"`|
|Set editor (optional)|`git config --global core.editor "editor"`|
|Check configuration|`git config --list`|
## The Core Workflow

Git stores your files in a **repository**. The process of saving work involves three main areas:

1. **Working Directory**: Where you currently edit files. If Git isn't watching a file yet, it is **untracked**.
2. **Index (Staging Area)**: Where changes are prepared before saving.
3. **Object Database**: Where Git permanently stores snapshots of your project.

**Initialize a Repository**
```bash
git init
```

**Tell Git to track a file (moves it to the Index)**
```bash
git add <file_name>
```

**Save the Index into the Object Database (creates a commit)**
```bash
git commit -m "Your message here"
```

<div style="page-break-after: always;"></div>

**Check the current state of your repository**
```bash
git status
```

After a successful commit, your working directory is considered ==**clean**==.

## Branching and Merging

A **branch** is a separate line of development. Every branch points to a specific **commit ID**.

#### Core Concepts
- **HEAD** is a pointer to the commit you are currently working on.
- **Switching branches**  with `git switch <branch>`  or `git checkout <branch>`  moves HEAD to another branch.
- **Merging**  combines changes from one branch into another.

#### Types of Merges

- **Fast-forward merge** happens when the target branch has not changed since the branch was created. Git simply moves the branch pointer forward.
- **Merge conflict** occurs when two branches modify the same line in the same file. The conflict must be resolved manually in an **editor** before the merge can be completed.

## Logging and Diffing

To understand your project's history, use these tools:

|Command|Text|
|---|---|
|`git log`|Lists the commits made on a branch.|
|`git log --oneline`|Shows a shorter version (one line per commit).|
|`git log --graph`|Visualizes the history as a diagram.|
|`git diff`|Compares the **Working Directory** with the **Index**.|
|`git diff --cached`|Compares the **Index** with the **Object Database**.|

## Undoing Changes and Referencing Parents

Git provides several ways to fix mistakes. To navigate history, you use special characters with **HEAD**.  An **Asterisk** is a character that appears in the git branch output to tell you where HEAD is.

```bash
* main   
  feature-login   
  test
```

<div style="page-break-after: always;"></div>

#### Referencing Commits

```bash
HEAD~1
HEAD~n
HEAD^
HEAD^2
```

- **Tilde (~)**: Used to go back a specific number of generations (e.g., `HEAD~1` is the first parent).
- **Caret (^)**: Used to specify which parent to follow in a merge commit (e.g., `HEAD^2` is the second parent).
- `HEAD~1` one commit before the current commit
- `HEAD~n` n commits before the current commit
- `HEAD^` first parent of a merge commit
- `HEAD^2` second parent of a merge commit

#### Commands for Fixing Mistakes
| Command                       | Description                                                                                  |
| ----------------------------- | -------------------------------------------------------------------------------------------- |
| `git restore <file>`          | Discards changes in the working directory and replaces them with the version from the Index. |
| `git restore --staged <file>` | Removes a file from the Index, replacing it with the last committed version.                 |
| `git commit --amend`          | Fixes a mistake in the last commit message (requires a clean working directory).             |
| `git revert`                  | Creates a new “anti-commit” that reverses the changes of a previous commit.                  |
| `git reset`                   | Moves HEAD and the current branch to a specific commit.                                      |
| `git reset --soft`            | Deletes the commit, but keeps changes in the Index.                                          |
| `git reset --mixed`           | Deletes the commit, but keeps changes in the Working Directory.                              |
| `git reset --hard`            | Deletes the commit and all changes. There is no going back.                                  |

# Remote Work and Collaboration

Working with others usually involves a hosting service like **GitHub**.

- **origin**: The default name for your remote repository.
- **clone**: Copy a remote repository to your local machine using `git clone <url>`
- **fork**: Create a copy of someone else's repository on your own GitHub account. It is a Github feature (not default Git feature)
- **fetch**: Downloads new branches and commits from the remote without merging them using `git fetch`
- **pull**: A combination of `fetch` and `merge`. It brings your local branch up to date with the remote using  `git pull`
- **push**: Sends your local commits to the remote repository using `git push`
- **Pull Request**: A request on GitHub to merge your changes into another branch.

<h2 style="page-break-before: always; page-break-after: avoid;">
Git and Terminal Command Reference
</h2>



| Category            | Command                                    | Description                                                                              |
| :------------------ | :----------------------------------------- | :--------------------------------------------------------------------------------------- |
| **Terminal Basics** | `mkdir`                                    | Creates a new directory (folder).                                                        |
|                     | `ls`                                       | Lists files and folders in the current directory.                                        |
|                     | `ls -A`                                    | Lists all files and folders, including hidden ones.                                      |
|                     | `pwd`                                      | "Print Working Directory" shows your current folder path.                              |
|                     | `cd ..\..`                                 | Navigates two directory levels up.                                                       |
| **Configuration**   | `git version`                              | Checks the currently installed version of Git.                                           |
|                     | `git config --global user.name "Name"`     | Sets the username for your commits.                                                      |
|                     | `git config --global user.email "mail"`    | Sets the email address for your commits.                                                 |
|                     | `git config --global core.editor "editor"` | Sets the default text editor for commit messages.                                        |
|                     | `git config --list`                        | Shows all current Git configuration settings.                                            |
| **Initialization**  | `git init`                                 | Initializes a new local Git repository in the current folder.                            |
|                     | `git clone <url>`                          | Copies an existing remote repository to your local machine.                              |
| **Basic Workflow**  | `git status`                               | Shows the state of the working directory and staging area (index).                       |
|                     | `git add <file>`                           | Adds a specific file to the staging area (index).                                        |
|                     | `git add .`                                | Adds all changes in the current directory to the staging area.                           |
|                     | `git commit -m "msg"`                      | Saves the staged changes as a new snapshot in the object database.                       |
|                     | `git commit --amend -m "msg"`              | Modifies the last commit message or includes forgotten changes.                          |
| **History & Logs**  | `git log`                                  | Lists the commit history of the current branch.                                          |
|                     | `git log --oneline`                        | One line per commit with shortened IDs.                                                  |
|                     | `git log --graph`                          | Visualizes the commit history as a diagram.                                              |
|                     | `git log --all`                            | Displays commit history for all branches.                                                |
|                     | `git log --abbrev-commit`                  | Shows shortened commit IDs.                                                              |
|                     | `git log --all --graph --oneline`          | Compact graphical overview of all branches.                                              |
|                     | `git log --pretty=oneline`                 | Shows one commit per line using the pretty format. |
|                     | `git rev-list --count HEAD`                | Counts the total number of commits on the current branch.                                |
| **Diffing**         | `git diff`                                 | Compares the working directory with the staging area (index).                            |
|                     | `git diff --cached`                        | Compares the staging area with the last commit.                                          |
|                     | `git diff --word-diff`                     | Word-by-word comparison instead of line-by-line.                                         |
|                     | `git diff <branch-a> <branch-b>`           | Shows differences between two branches.                                                  |
|                     | `git diff <branch-b>`                      | Shows differences between the current branch (HEAD) and `<branch-a>`. |
|                     | `git diff <id1> <id2>`                     | Compares two specific commits.                                                           |
|                     | `git diff HEAD~1 HEAD`                     | Compares the previous commit with the current commit. |
| **Branching**       | `git branch`                               | Lists all local branches.                                                                |
|                     | `git branch -v`                            | Lists branches with last commit message.                                                 |
|                     | `git branch -a`                            | Lists local and remote-tracking branches.                                                |
|                     | `git branch <name>`                        | Creates a new branch.                                                                    |
|                     | `git branch -m <old> <new>`                | Renames a branch.                                                                        |
|                     | `git branch -d <branch>`                   | Deletes a merged local branch.                                                           |
|                     | `git branch -vv`                           | Shows branches with upstream tracking info.                                              |
|                     | `git branch --all`                         | Lists local and remote-tracking branches. |
|                     | `git switch <branch>`                      | Switches HEAD to another branch (modern).                                                |
|                     | `git switch -c <branch>`                   | Creates and switches to a new branch (modern).                                           |
|                     | `git checkout <branch>`                    | Older command to switch branches.                                                        |
|                     | `git checkout -b <branch>`                 | Creates and switches to a new branch (legacy).                                           |
| **Merging**         | `git merge <branch>`                       | Integrates changes from another branch.                                                  |
| **Undoing & Files** | `git restore <file>`                       | Restores file in working directory from index.                                           |
|                     | `git restore --staged <file>`              | Removes file from index.                                                                 |
|                     | `git mv <old> <new>`                       | Renames or moves a file.                                                                 |
|                     | `git rm <file>`                            | Deletes a tracked file.                                                                  |
|                     | `git revert <commit>`                      | Creates an anti-commit that undoes changes.                                              |
|                     | `git reset --soft HEAD~n`                  | Removes commits, keeps changes staged.                                                   |
|                     | `git reset --mixed HEAD~n`                 | Removes commits, keeps changes unstaged.                                                 |
|                     | `git reset --hard HEAD~n`                  | Removes commits and deletes all changes.                                                 |
| **Remotes**         | `git remote`                               | Lists configured remotes.                                                                |
|                     | `git remote add origin <url>`              | Adds a remote repository.                                                                |
|                     | `git fetch`                                | Downloads remote changes without merging.                                                |
|                     | `git fetch --prune` or `-p`                | Removes deleted remote-tracking branches.                                                |
|                     | `git pull`                                 | Fetches and merges remote changes.                                                       |
|                     | `git push`                                 | Uploads commits to the remote.                                                           |
|                     | `git push origin --delete <branch>`        | Deletes a remote branch.                                                                 |                                                                                         |
|                     | `git push -u origin <branch>`              | Pushes a branch and sets the upstream tracking branch.             |
|                     | `git branch --set-upstream-to=origin/<branch>` | Sets the upstream branch for the current local branch.         |
|                     | `git branch --unset-upstream`              | Removes the upstream tracking branch from the current branch.     |
