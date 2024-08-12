# Git-Cheat-Sheet
A cheat sheet for Git commands 

## View
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git config -l                               | List already configured setup| 
| &#x2714; | git status                                  | Show the working tree status
| &#x2714; | git log                                     | See commit list |
| &#x2714; | git log --patch                             | See commit list and line changes |
| &#x2714; | git log --decorate --graph --oneline        | See commit visualization |
| &#x2714; | git log --grep **WORD**                     | See commits with <WORD> in the message |
| &#x2714; | git branch                                  | List all branches|
| &#x2714; | git branch -a                               | List all branches Local and Remote|
| &#x2714; | git branch --merged                         | Show branched merged into current branch |
| &#x2714; | git branch --no-merged                      | Show branched NOT merged into current branch |
| &#x2714; | git branch -vv                              | Check if upstream is set |
| &#x2714; | git show HEAD                               | Show the current commit |
| &#x2714; | git show **Branchname**                     | Show the last commit in a branch |
| &#x2714; | git show **Commit-hash**                    | Show specific commit |
| &#x2714; | git blame **FileName**                      | See who changed each line and when |
| &#x2714; | git blame --committer -L 1,3 **FileName**   | Shows commiter of the change, on specified lines|
| &#x2714; | git blame **Head FileName**                 | Check the previous commit for more insight|
| &#x274C; | git tag -l                                  | List tags with a pattern |
| &#x274C; | git tag -n                                  | List tags with annotations |
| &#x274C; | git show <tagname                           | Show the tag details |

| &#x274C; | git stash list                              | List stashes |
| &#x274C; | git stash show                              | Show the changes recorded in the stash |

| &#x2714; | git remote -v                               | List remote repositories |
| &#x2714; | git remote show **RepoName**                | Show remote repository details |

## Help 
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git --help                                  |  | 
| &#x2714; | git config                                  |  |
| &#x2714; | git **Command** --help                      |  |

## Configuration
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git config --global user.name **UserName**  | Set user name |
| &#x2714; | git config --global user.email **email**    | Set user email |

## Repository
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git clone **https://github.com/sampleURL.git**     | copy remote repository to local |
| &#x2714; | git init                                           | initiate new local repository and then create a remote repository and add remote's address to the local as origin |

## Remote to Local
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x274C; | git fetch                               | downloads everything from remote branch to the remote tracking branch |
| &#x274C; | git fetch **RepoName BranchName**     | downloads everything from remote specified branch to the remote tracking branch |
| &#x274C; | git pull                                | downloads everything from remote branch to the current branch in working directory |
| &#x274C; | git pull --rebase --prune               | Get latest, rebase any changes not checked in and delete branches that no longer exist | 

| &#x2714; | git clone *url*                       | Clone a repository into a new directory |
| &#x2714; | git clone *url* **directory**         | Clone a repository into a specific directory |

## Staged Changes
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git add **FileName**                        | Stage file |
| &#x2714; | git add -p **FileName**            | Stage some but not all changes in a file |
| &#x2714; | git reset **FileName**                          | Unstage changes | 
| &#x2714; | git reset --soft **commit** | Moves the Head to the specified commit, Leaves stagging and working dir. unchanged |
| &#x2714; | git reset --mixed **commit** | Moves the Head to the specified commit, files are unstaged and working dir. remains unchanged |
| &#x2714; | git reset --hard **commit** | Moves the Head to the specified commit, all changes after the specified commit are discarded |
| &#x274C; | git clean -f\|--force -d                | Recursively remove untracked files from the working tree |
| &#x274C; | git clean -f\|--force -d -x             | Recursively remove untracked and ignored files from the working tree |

## Changing Commits
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git commit -m "**Message**"   | Add files to Local Repo which were staged |
| &#x2714; | git commit -am "**Message**"  | Add files to Local Repo which were NOT staged |
| &#x2714; | git commit --amend -m "New message"         | Change the last commit message |
| &#x274C; | git commit --fixup 5720fdf -m "New message" | Merge into the specified commit |
| &#x274C; | git revert 5720fdf                          | Revert a commit |
| &#x274C; | git rebase --interactive [origin/main]      | Rebase a PR (`git pull` first) |
| &#x274C; | git rebase --interactive 5720fdf            | Rebase to a particular commit |
| &#x274C; | git rebase --interactive --root 5720fdf     | Rebase to the root commit |
| &#x274C; | git rebase --continue                       | Continue an interactive rebase |
| &#x274C; | git rebase --abort                          | Cancel an interactive rebase |
| &#x274C; | git rebase **Branchname**     Reapply commits on top of another base tip
| &#x274C; | git rebase --interactive <base>       Interactively rebase the current branch onto another base
| &#x274C; | git cherry-pick **Commit-hash**            Apply the changes introduced by some existing commits
| &#x274C; | git cherry-pick --abort           Abort the cherry-pick process
| &#x274C; | git cherry-pick --continue           Continue the cherry-pick process after resolving conflicts

## Compare
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git diff                                | See new updattes on files made after previous move |
| &#x2714; | git diff --staged                       | See difference between stagged area and committed area |
| &#x2714; | git diff HEAD                           | See difference between current commit and previous commit |
| &#x2714; | git diff HEAD^^..HEAD^                  | See difference between specified commits |
| &#x2714; | git diff *Branch**1** Branch**2***      | See difference between two branches |

## Local to Remote
| - | Command | Description |
| &#x2714; / &#x274C; | Command | Description |
| &#x2714; | git push                                       Update remote refs along with associated objects
| &#x2714; | git push -u **RepoName BranchName**     Push a branch and set upstream.
| &#x2714; | git push **RepoName BranchName**                Push a branch to the remote repository
| &#x2714; | git push --force                        | Push any changes while overwriting any remote changes |
| &#x2714; | git push --force-with-lease             | Push any changes but stop if there are any remote changes |
| &#x2714; | git push --tags                         | Push tags to remote repository |
| &#x2714; | git push **RepoName** --delete **BranchName**  | Delete branch from remote after deleting from local |
| &#x2714; | git remote add **RepoName** *url*             | Add remote referance on local directory for accessbility to remote repo |
| &#x2714; | git remote remove **RepoName**        | Remove remote referance from local directory for accessbility to remote repo|

| &#x2714; | git fetch upstream                      | Fetch all remote branches |
| &#x2714; | git rebase upstream/main                | Refresh main branch from upstream |



## Branching and Mearging
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git branch **Branchname**                 | Create a new branch |
| &#x2714; | git branch -d **Branchname**              | Deletes a branch |
| &#x2714; | git switch **Branchname**                 | Switch to a branch |
| &#x2714; | git switch -c **Branchname**              | Create and switch to a branch |
| &#x2714; | git branch -m  **NEW-BranchName**         | Rename Current Branch|

| &#x2714; | git merge **Branchname**                  | Merge branch into current branch |
| &#x2714; | git merge origin/**Branchname**           | Merge the referance(Remote-Tracking Branches) from remote branch into current branch|
| &#x2714; | git merge --no-ff **Branchname**    Merge with a merge commit even if a fast-forward merge is possible
| &#x2714; | git merge --squash **Branchname**    Merge a branch into the current branch but do not create a commit
| &#x2714; | git merge --abort                  Abort the merge process and try to reconstruct the pre-merge state
| &#x2714; | git mergetool               Run merge conflict resolution tools to resolve merge conflicts



## Stash
| &#x2714; / &#x274C; | Command | Description |
| - | - | - | 
git stash                  Stash the changes in a dirty working directory away
| &#x2714; | git stash push -m "Message"             | Stash staged files |
| &#x2714; | git stash --include-untracked           | Stash working area and staged files |
| &#x2714; | git stash --staged                      | Stash staged files |
| &#x2714; | git stash apply                         | Moved last stash to working area |
| &#x2714; | git stash apply 0                       | Moved named stash to working area |
| &#x2714; | git stash clear                         | Clear the stash |
| &#x2714; | git stash pop` - Apply the changes recorded in the stash to the working directory and delete the stash
| &#x2714; | git stash drop` - Remove a single stashed state from the stash list

## Tags
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git tag                                              | List all tags |
| &#x2714; | git tag <tagname>                          Create a new tag
| &#x2714; | git tag -a\|--annotate 0.0.1 -m\|--message "Message" | Create a tag |
| &#x2714; | git tag -d\|--delete 0.0.1                           | Delete a tag |
| &#x2714; | git push --tags                                      | Push tags to remote repository |
| &#x2714; | git push origin <tagname>` - Push a tag to the remote repository
| &#x2714; | git push origin --delete <tagname>` - Delete a tag from the remote repository


## File Handling
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git mv
rm
| &#x2714; | git reset --staged **FileName**
| &#x2714; | git reset
| &#x2714; | git mv **FileName** **NEW-FileName**              | Move/rename file |
| &#x2714; | git rm --force **FileName**                 | Unstage and delete file |

## Submodules
| &#x2714; / &#x274C; | Command | Description |
| - | - | - |
| &#x2714; | git submodule status                    | Check status of all submodules |
- **`git submodule add <url>` - Add a submodule.**
- **`git submodule init` - Initialize the submodule configuration.**
- **`git submodule update` - Fetch and checkout the submodule.**
- **`git submodule deinit <path>` - Deinitialize a submodule.**
- **`git submodule status` - Show the status of submodules.**
- **`git submodule sync` - Synchronize submodule URLs.**
- **`git submodule foreach <command>` - Execute a command in each submodule.**


## Advanced Commands
Commands for advanced Git operations.

- `git bisect` - Use binary search to find the commit that introduced a bug.
  - `git bisect start` - Start the bisect process.
  - `git bis

