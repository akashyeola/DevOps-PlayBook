# Git-Cheat-Sheet
A cheat sheet for Git commands 

## Help 
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
git --help
git config


## Configuration
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git config --global user.name **UserName**              | Set user name |
| &#x2714; | git config --global user.email **email**                | Set user email |

| &#x2714; | git remote add origin <url>                             | Add remote origin for local directory for accessbility to remote repo |
| &#x2714; | git push -u origin **REMOTE-BranchName**                | To set upstream for a perticular branch |

## Repository
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git clone **https://github.com/sampleURL.git**     | copy remote repository to local |
| &#x2714; | git init                                           | initiate new local repository and then create a remote repository and add remote's address to the local as origin |


## View
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
git config -l  | List already configured setup| 
| &#x2714; | git branch                              | list all branches|
| &#x2714; | git branch -a                           | list all branches Local and Remote|
| &#x2714; | git branch --merged                     | Show branched merged into current branch |
| &#x2714; | git branch --no-merged                  | Show branched NOT merged into current branch |
| &#x2714; | git branch -vv                          | Check if upstream is set |
| &#x2714; | git log                                 | See commit list |
| &#x2714; | git log --patch                         | See commit list and line changes |
| &#x2714; | git log --decorate --graph --oneline    | See commit visualization |
| &#x2714; | git log --grep **WORD**                   | See commits with <WORD> in the message |
| &#x2714; | git show HEAD                             | Show the current commit |
| &#x2714; | git show HEAD^                            | Show the previous commit |
| &#x2714; | git show HEAD^^                           | Show the commit going back two commits |
| &#x2714; | git show **Branchname**                   | Show the last commit in a branch |
| &#x2714; | git show **Commit-hash>**                 | Show specific commit |
| &#x2714; | git blame **FileName**                    | See who changed each line and when |
| &#x2714; | git blame --committer -L 1,3 **FileName**   | shows commiter of the change, on specified lines|
| &#x2714; | git blame **Head^** **FileName**            | Check the previous commit for more insight|

## Compare
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git diff                                | See new updattes on files made after previous move |
| &#x2714; | git diff --staged                       | See difference between stagged area and committed area |
| &#x2714; | git diff HEAD                           | See difference between current commit and previous commit |
| &#x2714; | git diff HEAD^^..HEAD^                  | See difference between specified commits |
| &#x2714; | git diff *Branch**1** Branch**2***      | See difference between two branches |

## Branching and Mearging
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git branch **Branchname**                 | Create a new branch |
| &#x2714; | git branch -d **Branchname**              | Deletes a branch |
| &#x2714; | git switch **Branchname**                 | Switch to a branch |
| &#x2714; | git switch -c **Branchname**              | Create and switch to a branch |
| &#x2714; | git branch -m  **NEW-BranchName**         | Rename Current Branch|
| &#x2714; | git push -u origin **REMOTE-BranchName**  | To set upstream for a perticular branch |
| &#x2714; | git restore **FileName**                      | Undo all changes on the foo.js file |
| &#x2714; | git merge **Branchname**                  | Merge branch into current branch |
| &#x2714; | git merge origin/**Branchname**           | Merge the referance(Remote-Tracking Branches) from remote branch into current branch|

## Remote to Local
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git fetch                               | downloads everything from remote branch to the remote tracking branch |
| &#x2714; | git pull                                | downloads everything from remote branch to the current branch in working directory |
| &#x2714; | git pull --rebase --prune               | Get latest, rebase any changes not checked in and delete branches that no longer exist | 

## Staged Changes
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git add **FileName**                        | Stage file |
| &#x2714; | git add -p **FileName**            | Stage some but not all changes in a file |
| &#x2714; | git mv **FileName** **NEW-FileName**              | Move/rename file |
| &#x2714; | git rm --force **FileName**                 | Unstage and delete file |
| &#x2714; | git reset HEAD                          | Unstage changes | 
| &#x2714; | git reset --hard HfEAD                  | Unstage and delete changes |
| &#x2714; | git clean -f\|--force -d                | Recursively remove untracked files from the working tree |
| &#x2714; | git clean -f\|--force -d -x             | Recursively remove untracked and ignored files from the working tree |

## Changing Commits
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
git reset --soft **commit** | Moves the Head to the specified commit, Leaves stagging and working dir. unchanged |
git reset --mixed **commit** | Moves the Head to the specified commit, files are unstaged and working dir. remains unchanged |
git reset --hard **commit** | Moves the Head to the specified commit, all changes after the specified commit are discarded |
git commit -m "**Message**"   | Add files to Local Repo which were staged |
git commit -am "**Message**"  | Add files to Local Repo which were NOT staged |
| &#x2714; | git commit --amend -m "New message"         | Change the last commit message |
| &#x2714; | git commit --fixup 5720fdf -m "New message" | Merge into the specified commit |
| &#x2714; | git revert 5720fdf                          | Revert a commit |
| &#x2714; | git rebase --interactive [origin/main]      | Rebase a PR (`git pull` first) |
| &#x2714; | git rebase --interactive 5720fdf            | Rebase to a particular commit |
| &#x2714; | git rebase --interactive --root 5720fdf     | Rebase to the root commit |
| &#x2714; | git rebase --continue                       | Continue an interactive rebase |
| &#x2714; | git rebase --abort                          | Cancel an interactive rebase |
| &#x2714; | git cherry-pick 5720fdf                     | Copy the commit to the current branch |

## Stash
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git stash push -m "Message"             | Stash staged files |
| &#x2714; | git stash --include-untracked           | Stash working area and staged files |
| &#x2714; | git stash --staged                      | Stash staged files |
| &#x2714; | git stash list                          | List stashes |
| &#x2714; | git stash apply                         | Moved last stash to working area |
| &#x2714; | git stash apply 0                       | Moved named stash to working area |
| &#x2714; | git stash clear                         | Clear the stash |

## Tags
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git tag                                              | List all tags |
| &#x2714; | git tag -a\|--annotate 0.0.1 -m\|--message "Message" | Create a tag |
| &#x2714; | git tag -d\|--delete 0.0.1                           | Delete a tag |
| &#x2714; | git push --tags                                      | Push tags to remote repository |

## Remote
| - | Command | Description |
| - | - | - |
| &#x2714; | git remote add <RepoName> <url>             | Add remote referance on local directory for accessbility to remote repo |
| &#x2714; | git remote remove <Origin/Other>        | Remove remote referance from local directory for accessbility to remote repo|
| &#x2714; | git remote -v                           | List remote repositories |
| &#x2714; | git remote show origin                  | Show remote repository details |
| &#x274C; | git remote add upstream <url>           | Add remote upstream repository |
| &#x2714; | git fetch upstream                      | Fetch all remote branches |
| &#x2714; | git rebase upstream/main                | Refresh main branch from upstream |
| &#x2714; | git remote -v                           | List remote repositories |
| &#x2714; | git push --force                        | Push any changes while overwriting any remote changes |
| &#x2714; | git push --force-with-lease             | Push any changes but stop if there are any remote changes |
| &#x2714; | git push --tags                         | Push tags to remote repository |
| &#x2714; | git push origin --delete <branch-name>  | Delete branch from remote after deleting from local |

## File Handling
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
git mv
rm
git reset --staged **FileName**
git reset

## Submodules
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git submodule status                    | Check status of all submodules |

- Pull submodules
  1. git submodule sync
  2. git submodule init
  3. git submodule update
- Change branch
  1. cd /submodule
  2. git fetch origin <branch-name>
  3. git checkout <branch-name>
  4. cd /

# Notes



----------------------------

## 1. View
Commands that help you view the status, logs, differences, etc.

- `git status` - Show the working tree status.
- `git log` - Show commit logs.
- `git log --oneline` - Show a summarized log.
- `git log --graph` - Show a graph of the commit history.
- `git log --stat` - Show stats of changes in each commit.
- `git diff` - Show changes between commits, commit and working tree, etc.
  - `git diff --staged` - Show changes between the index and the last commit.
  - `git diff <commit>` - Show changes between the working directory and a specific commit.
  - `git diff <commit1> <commit2>` - Show changes between two commits.
- `git show` - Show various types of objects.
  - `git show <commit>` - Show changes made in a specific commit.
  - `git show <branch>:<file>` - Show a file from a specific branch.
- `git branch` - List, create, or delete branches.
  - `git branch -a` - List all branches (local and remote).
  - `git branch -r` - List remote branches only.
- `git tag` - List, create, or delete tags.
  - `git tag -l` - List tags with a pattern.
  - `git tag -n` - List tags with annotations.
- `git blame` - Show what revision and author last modified each line of a file.
  - `git blame <file>` - Show blame information for a file.
  - **`git blame <commit> <file>` - Show blame information for a file at a specific commit.**

## 2. Local to Remote
Commands to push changes from the local repository to the remote repository.

- `git push` - Update remote refs along with associated objects.
  - `git push origin <branch>` - Push a branch to the remote repository.
  - `git push -u origin <branch>` - Push a branch and set upstream.
  - `git push origin --delete <branch>` - Delete a branch in the remote repository.
  - **`git push --tags` - Push all tags to the remote repository.**
- `git remote add <name> <url>` - Add a remote repository.
- `git remote remove <name>` - Remove a remote repository.
- `git remote set-url <name> <newurl>` - Change the URL of a remote repository.
- `git remote -v` - Show the list of remote repositories.

## 3. Remote to Local
Commands to fetch or pull changes from the remote repository to the local repository.

- `git fetch` - Download objects and refs from another repository.
  - `git fetch <remote>` - Fetch from a specific remote repository.
  - **`git fetch <remote> <branch>` - Fetch a specific branch from a remote repository.**
- `git pull` - Fetch from and integrate with another repository or a local branch.
  - **`git pull --rebase` - Rebase the current branch on top of the upstream branch after fetching.**
- `git clone <url>` - Clone a repository into a new directory.
  - `git clone <url> <directory>` - Clone a repository into a specific directory.

## 4. Branch
Commands to manage branches.

- `git branch` - List, create, or delete branches.
  - `git branch <branch>` - Create a new branch.
  - `git branch -d <branch>` - Delete a branch.
  - `git branch -D <branch>` - Force delete a branch.
  - **`git branch --move <old-branch> <new-branch>` - Rename a branch.**
  - `git branch --set-upstream-to=<remote>/<branch> <branch>` - Set up tracking information.
- `git checkout <branch>` - Switch branches or restore working tree files.
  - `git checkout -b <branch>` - Create and switch to a new branch.
  - `git checkout <commit> -- <file>` - Checkout a specific file from a commit.
- `git switch <branch>` - Switch branches.
  - `git switch -c <branch>` - Create and switch to a new branch.

## 5. Merge
Commands to merge branches and resolve conflicts.

- `git merge <branch>` - Join two or more development histories together.
  - `git merge --no-ff <branch>` - Merge with a merge commit even if a fast-forward merge is possible.
  - **`git merge --squash <branch>` - Merge a branch into the current branch but do not create a commit.**
  - `git merge --abort` - Abort the merge process and try to reconstruct the pre-merge state.
- `git rebase <branch>` - Reapply commits on top of another base tip.
  - `git rebase --interactive <base>` - Interactively rebase the current branch onto another base.
  - `git rebase --abort` - Abort the rebase process.
  - `git rebase --continue` - Continue the rebase process after resolving conflicts.
- `git cherry-pick <commit>` - Apply the changes introduced by some existing commits.
  - **`git cherry-pick --abort` - Abort the cherry-pick process.**
  - **`git cherry-pick --continue` - Continue the cherry-pick process after resolving conflicts.**
- **`git mergetool` - Run merge conflict resolution tools to resolve merge conflicts.**

## 6. Staging and Commit
Commands to stage and commit changes.

- `git add <file>` - Add file contents to the index (staging area).
- `git add -A` - Add all changes to the index.
- `git add .` - Add current directory contents to the index.
- **`git add -p` - Interactively choose hunks of patch between the index and the work tree.**
- `git commit -m "message"` - Record changes to the repository with a message.
- **`git commit -a -m "message"` - Commit all changes with a message.**
- `git commit --amend` - Amend the previous commit.
  - `git commit --amend -m "message"` - Amend the previous commit with a new message.
- `git reset <file>` - Unstage a file while retaining the changes in the working directory.
- `git reset --soft <commit>` - Reset the current branch to the specified commit, keeping changes staged.
- `git reset --hard <commit>` - Reset the current branch to the specified commit, discarding all changes.
- **`git reset HEAD~1` - Undo the last commit while keeping changes in the working directory.**
- **`git restore --staged <file>` - Unstage a file while retaining the changes in the working directory.**

## 7. File Operations
Commands to manage files in the repository.

- `git rm <file>` - Remove files from the working tree and from the index.
  - `git rm --cached <file>` - Remove files from the index only.
- `git mv <old> <new>` - Move or rename a file, a directory, or a symlink.
- **`rm <file>` - Delete a file from the working directory using a terminal command.**

## 8. Stash
Commands to temporarily save changes.

- `git stash` - Stash the changes in a dirty working directory away.
  - `git stash list` - List all stashed changesets.
  - `git stash pop` - Apply the changes recorded in the stash to the working directory and delete the stash.
  - `git stash apply` - Apply the changes recorded in the stash to the working directory without deleting the stash.
  - `git stash drop` - Remove a single stashed state from the stash list.
  - `git stash clear` - Remove all the stashed states.
  - **`git stash show` - Show the changes recorded in the stash.**

## 9. Tags
Commands to create, list, delete, and verify tags.

- `git tag` - List tags.
  - `git tag <tagname>` - Create a new tag.
  - `git tag -a <tagname> -m "message"` - Create an annotated tag.
  - `git tag -d <tagname>` - Delete a tag.
- `git show <tagname>` - Show the tag details.
- `git push origin <tagname>` - Push a tag to the remote repository.
- **`git push origin --delete <tagname>` - Delete a tag from the remote repository.**

## 10. Submodules
Commands to manage submodules.

- **`git submodule add <url>` - Add a submodule.**
- **`git submodule init` - Initialize the submodule configuration.**
- **`git submodule update` - Fetch and checkout the submodule.**
- **`git submodule deinit <path>` - Deinitialize a submodule.**
- **`git submodule status` - Show the status of submodules.**
- **`git submodule sync` - Synchronize submodule URLs.**
- **`git submodule foreach <command>` - Execute a command in each submodule.**

## 11. Advanced Commands
Commands for advanced Git operations.

- `git bisect` - Use binary search to find the commit that introduced a bug.
  - `git bisect start` - Start the bisect process.
  - `git bis