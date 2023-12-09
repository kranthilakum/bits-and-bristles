---
title: Git cheatsheet
date: 2021-03-10T09:55:46+05:30
draft: false
categories:
- "git"
tags:
- "git"
- "cheatsheet"
---

### Typical Git Workflow

-   Clone a remote repository
-   Create a branch with a name to commit any changes that you plan to make in your local workspace
-   Commit your changes to the branch. It is also possible to have multiple commits or squash several commits into one commit.
-   Tag your commit, if needed.
-   Rebase your branch with master branch to resolve any possible merge conflicts. Merge conflicts may appear in your branch when other people may have introduced additional changes to the files which you had modified as part of your work.
-   Push your branch to the remote repository
-   Create a pull request so that others can review your changes. If you receive any comments from the reviewers, you might need to make additional commits to incorporate reviewers feedback and push your changes to your branch.
-   When the pull request is approved, you are allowed to merge your branch into the master branch so that your changes are made available to other people.

### General Configuration

**User details**

```
git config --global user.name "<user name>"
git config --global user.email "<user@email.com>"
```

### Aliasing Git commands

Aliases are used to create shorter commands that map to longer commands. Aliases enable more efficient workflows by requiring fewer keystrokes to execute a command.

```
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

**Default configuration for future merge conflicts**

```
git config --global merge.conflictstyle diff3
```

### Cloning

**Clone a remote repository**

```
git clone <repository-URL>
```

**Clone a remote repository and checkout to a specific branch.**

```
git clone -o <user-defined-remote-name> -b <branch-to-checkout>\
<http[s|]ssh|git|ftp[s]>://<repository-url> <directory>

git clone --origin enzyme --branch gh-pages --progress\
git@github.com:airbnb/enzyme.git enzyme
```

**Clone a bare Git repository.**

```
git clone --bare git@github.com:lodash/lodash.git
```

**Don't clone any tags**

```
git clone git@github.com:lodash/lodash.git --no-tags
```

**NOTE:** Cloning into an existing directory is only allowed if the is empty.

### Staging and Unstaging

**Add file(s) to staging area**

```
git add <file-name-1> ... <file-name-n>
```

**Remove file(s) from working tree and from staging area** This will not remove file(s) from working directory

```
git rm <file-name(s)>
```

### Snapshotting

**Commit file change(s) added to staging area**

```
git commit -m <commit-message>
```

**Change the most recent commit** The command lets you combine staged changes with the previous commit instead of creating an entirely new commit.

```
git commit --amend
```

**Undo most recent commit**

```
git reset --soft HEAD~1
```

**Remove most recent commit**

```
git reset --hard HEAD~1
```

**Revert a recently made upstream commit**

```
git revert HEAD~
```

**Revert a recently made merge commit**

```
git revert -m
```

**Recover a removed commit**

```
git reflog
git checkout -b <branch-name> <commit-ID-which-was-removed>
```

### Pulling

-   `fetch`, which downloads the changes from your remote repo but does not apply them to your code.
-   `merge`, which applies changes taken from `fetch` to a branch on your local repo.
-   `pull`, which is a combined command that does a `fetch` and then a `merge`.

```
# pull = fetch + merge
git checkout <branch>
git fetch
git merge

# pull changes to a specific branch
git pull <remote> <branch>

# pull rebase
git pull --rebase
```

### Sharing

force push to master branch (if remote allows it)

```
git push [-f/--force] origin master
```

**Force push to only one branch**

```
git push origin +<branch-name>
```

### Inspecting

```
git status -sb
```

what you had in your branch before the merge

```
git diff --ours -b
```

what was on their side

```
git diff --theirs -b
```

how a file has changed from both sides

```
git diff --base -b
```

see tag data along with commit information

```
git show <tag-name>
```

```
git ls-files
```

your repository will be back to the last committed state

```
git reset --hard HEAD
```

### Logging

full list of all of the unique commits that were included in either branch involved in a merge

```
git log --oneline --left-right HEAD...MERGE_HEAD
```

```
git log --graph --oneline --decorate --all
```

when you need information on the history of a file

```
git log --merge --decorate --source -p path/to/file/you/care/about
```

re-checkout file and replace merge conflict markers with ours, base and theirs

```
git checkout --conflict=diff3 <filename>
```

### Stashing

**Store away your workspace**

```
git stash save "<stash-name>"
```

**Re-apply stored workspace**

```
git stash apply "<stash-name>"
```

**Delete stored workspace**

```
git stash drop "<stash-name>"
```

### Cleaning

clear out extra files created due to merge but no longer need

```
git clean -fd
```

### Branching

**Create a new local branch and push it upstream**

```
git checkout -b <branch-name>
git push --set-upstream origin <branch-name>
git push -u origin <branch-name>
```

**Check if commit exists in your local branch**

```
git branch -a --contains <commit-id>
```

**Rename your local branch**

```
git branch -m <old-branch-name> <new-branch-name>
```

**Rename remote branch**

```
git push <remote-name> :<old-branch-name> <new-branch-name>
git push origin -u <new-branch-name>
```

### Tagging

**Create a new tag**

```
git tag -a <tag-annotation> -m <tag-name>
```

**Tag a commit**

```
git tag -a <tag-annotation> <commit-ID>
```

**Push a tag to upstream repository**

```
git push origin <tag-name>
```

**Push all tags to upstream repository**

```
git push origin --tags
```

**Checkout to tag (Detached HEAD mode)**

```
git checkout <tag-name>
```

**Create a branch from a tagged commit and checkout to the branch**

```
git checkout -b <brach-name> <tag-name>
```

### Merging

**Merge one branch into another**

```
git checkout <target-branch>
git merge <source-branch>
```

### Dealing with Merge Conflicts

There are three kinds of conflicts:

-   File deleted and changed Use modified or deleted file?
-   File deleted and created Use created or deleted file?
-   File changed both locally and remotely Start merge tool.

Four versions of the same file: | Base | The latest version of the file that exist in both repositories | | Local | The latest local version of the file | | Remote | The latest remote version of the file | | Merged | The result of the merge |

### Rebasing

Use rebase to update your branch with the latest changes from the main branch.

### Squashing

With `rebase`, you can condense the changes made in a set of commits down to one single commit. Squashing is useful to clean up the commit history before they are pushed to a remote branch.

```
git rebase -i HEAD~2

---
pick eb45fef Updated app.js
squash 01843df Updated README.md
```

### Cherry-Picking

Use cherry-pick to copy commits from one branch to another. Cherry-pick only brings the changes from the commits you select, instead of all the changes in a branch. With cherry-pick, you can pick a set of commits from the main branch (e.g. master) without rebasing your branch with the main branch.

```
git checkout <branch>
git cherry-pick <commit-id> # pick a commit from another branch
```

### Patching

```
git format-patch master --stdout > patch--001.patch
git checkout <branch>
git am patch-001.patch
```

### Debugging

Use `git blame` to determine which commit and committer was responsible for lines in a file.

```
git blame -L 23,15 README.md
```

Everyday Git
------------

-   `git clone` from an upstream repository to your local workspace repository.
-   `git checkout` to discard changes in local workspace.
-   `git checkout` and git-branch to switch branches.
-   `git add` to manage the file in staging area/index.
-   `git diff` and git-status to see what you are in the middle of doing.
-   `git commit` to advance the current branch.
-   `git reset` and git-checkout (with pathname parameters) to undo changes.
-   `git cherry-pick` to choose a commit from one branch and apply it onto another.
-   `git merge` to merge between local branches.
-   `git rebase` to maintain topic branches.
-   `git revert` to undo botched commits.
-   `git tag` to mark a known point.
-   `git pull` and `git fetch` from "origin" to keep up-to-date with the upstream.
-   `git request-pull` to create a summary of changes for your upstream to pull.
-   `git push` to publish your changes to shared repository.
-   `git format-patch` to prepare and send suggested alternatives to contributors via e-mail submission
-   `git send-email` to send your e-mail submission without corruption by your MUA.
-   `git am` to apply patches e-mailed in from your contributors.

Glossary
--------

-   **Repository** - a virtual storage of your project
-   **Downstream** - when you copy (clone, pull, etc.) from a repository
-   **Upstream** - when you send your changes to a repository
-   **Tree** - represents a particular directory state of a working directory
-   **Commit Tree** - repesents a commit object with zero or more number of parent commits. With no commit as parent, a commit will be a root commit. With a single parent, a commit will be an ordinary commit. With more than one parent, a commit will be a merge commit.
-   **Commit** - a snapshot or changeset, represents the state of a working directorry in "time", and explains how to get there
-   **HEAD** - a reference (ref) to the currently checked out commit
-   **Staging Area** - a file which stores information about what will go into your next commit
-   **Working Directory or Tree** - workspace
-   **History rewriting commands** - checkout, reset, revert

References
----------

-   [Git SCM PRO Book by Scott Chacon et al.](https://git-scm.com/book/)
-   [Resetting, Checking out, and Reverting](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting)
-   [Revert a faulty merge commit](https://www.kernel.org/pub/software/scm/git/docs/howto/revert-a-faulty-merge.txt)

-   [Github](https://www.github.com/kranthilakum)
-   [Linkedin](https://www.linkedin.com/in/kranthilakum/)
-   [StackOverflow](https://stackoverflow.com/users/1509209/kranthi-lakum)