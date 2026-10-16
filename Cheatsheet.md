# Git Cheat Sheet — Full (Beginner Friendly)

This cheat sheet lists commonly used Git commands with simple, plain-English explanations and short examples. Save this file as `git_cheatsheet.md`. A GitHub Action in this repo will convert it to `git_cheatsheet.pdf` automatically.

---

## Setup & Identity

- `git --version`
  - What it does: Shows the installed Git version.
  - Example: `git --version`

- `git config --global user.name "Your Name"`
  - What it does: Sets your name for commits.
  - Example: `git config --global user.name "Alice"`

- `git config --global user.email "you@example.com"`
  - What it does: Sets your email for commits.
  - Example: `git config --global user.email alice@example.com`

- `git config --global core.editor "code --wait"`
  - What it does: Sets the editor Git uses for commit messages.
  - Example: `git config --global core.editor "code --wait"`

- `git config --list`
  - What it does: Shows your Git configuration settings.


## Create, clone, basic repo

- `git init`
  - What it does: Starts a new Git repository in the current folder.
  - Example: `git init`

- `git clone <url>`
  - What it does: Copies a remote repository to your computer.
  - Example: `git clone https://github.com/user/repo.git`

- `git clone -b <branch> <url>`
  - What it does: Clone a specific branch from a repo.

- `git ls-files`
  - What it does: Lists files currently tracked by Git.


## Check status / viewing

- `git status`
  - What it does: Shows which files are changed, staged, or untracked.
  - Example: `git status`

- `git diff`
  - What it does: Shows changes in files you haven't staged yet.
  - Example: `git diff`

- `git diff --staged`
  - What it does: Shows the changes that are staged and ready to commit.

- `git show <commit>`
  - What it does: Shows details (diff) of a commit.
  - Example: `git show a1b2c3d`

- `git show <branch>:<path/to/file>`
  - What it does: Shows a file's contents from a commit or branch.


## Staging & Commit

- `git add <file>`
  - What it does: Marks a file to be included in the next commit (staging area).
  - Example: `git add README.md`

- `git add .`
  - What it does: Stage all changed files in the current folder.

- `git add -p`
  - What it does: Interactively choose hunks to stage (useful for partial commits).

- `git commit -m "message"`
  - What it does: Saves staged changes to your local repository with a short message.
  - Example: `git commit -m "Add README"`

- `git commit -a -m "message"`
  - What it does: Stages tracked files and commits them in one step (won't add new untracked files).

- `git commit --amend`
  - What it does: Replace the most recent commit (use to fix message or add missed changes).
  - Example: make change, `git add file`, then `git commit --amend --no-edit` to add to last commit.

- `git restore --staged <file>`
  - What it does: Unstage a file (remove from staging area).

- `git rm <file>`
  - What it does: Remove a file from the working tree and stage the deletion.

- `git mv <old> <new>`
  - What it does: Rename or move a tracked file.


## Branching & Switching

- `git branch`
  - What it does: List local branches.
  - Example: `git branch`

- `git branch -a`
  - What it does: List all branches, including remote branches.

- `git branch <name>`
  - What it does: Create a new branch.
  - Example: `git branch feature/login`

- `git switch <name>`
  - What it does: Switch to another branch (newer command).
  - Example: `git switch feature/login`

- `git switch -c <name>`
  - What it does: Create and switch to a branch in one step.
  - Example: `git switch -c feature/ui`

- `git checkout <name>`
  - What it does: Older way to switch branches and checkout commits.

- `git checkout -b <name>`
  - What it does: Create and switch to a branch (older command).

- `git branch -d <name>`
  - What it does: Delete a branch that has been merged.

- `git branch -D <name>`
  - What it does: Force delete a branch (use with caution).


## Merging & Resolving

- `git merge <branch>`
  - What it does: Merge another branch into the current branch (keeps history).
  - Example: `git merge feature/login`

- `git merge --no-ff <branch>`
  - What it does: Force a merge commit even if fast-forward is possible.

- `git merge --abort`
  - What it does: Stop a merge and return to the pre-merge state if conflicts happen.

- Resolving conflicts:
  - What to do: Edit files to fix conflicts (look for <<<<<<< markers), then `git add` the fixed files and `git commit`.


## Rebasing & History Rewriting (use with care)

- `git rebase <branch>`
  - What it does: Move your commits to be based on another branch (rewrite history locally).
  - Example: `git rebase main`

- `git rebase -i HEAD~N`
  - What it does: Interactive rebase to edit/squash/reorder the last N commits (useful to clean history).

- `git rebase --abort`
  - What it does: Cancel a rebase in progress and return to previous state.

- `git rebase --continue`
  - What it does: After resolving a conflict during rebase, continue it.

- `git reflog`
  - What it does: Shows a log of where HEAD has been — very useful to recover lost commits.

- `git reset --soft <commit>`
  - What it does: Move HEAD to a commit but keep changes staged.

- `git reset --mixed <commit>`
  - What it does: Move HEAD and unstage changes (default reset).

- `git reset --hard <commit>`
  - What it does: Move HEAD and discard all working changes — destructive.

- `git cherry-pick <commit>`
  - What it does: Apply a single commit from another branch onto the current branch.


## Undo / Recover

- `git restore <file>`
  - What it does: Discard local changes in a file (restore from HEAD).
  - Example: `git restore README.md`

- `git restore --source=<commit> <file>`
  - What it does: Restore a file from a specific commit.

- `git revert <commit>`
  - What it does: Create a new commit that undoes the changes in the given commit (safe for shared branches).

- `git reflog`
  - What it does: Find lost commits and see history of HEAD moves.

- `git clean -fd`
  - What it does: Remove untracked files and directories (dangerous — use with caution).


## Viewing History

- `git log`
  - What it does: Show commit history for the current branch.

- `git log --oneline --graph --decorate`
  - What it does: Compact, visual history useful for branches.

- `git log -p`
  - What it does: Show diffs for each commit.

- `git log --stat`
  - What it does: Shows file changes summary per commit.

- `git blame <file>`
  - What it does: Show the last commit that changed each line in the file.

- `git shortlog`
  - What it does: Summary of commits by author.


## Remotes

- `git remote -v`
  - What it does: List remote repositories and URLs.

- `git remote add origin <url>`
  - What it does: Add a remote named "origin" pointing to a URL.

- `git remote remove origin`
  - What it does: Remove a remote.

- `git fetch <remote>`
  - What it does: Download remote changes (no merge).

- `git fetch --all`
  - What it does: Fetch from all remotes.

- `git pull`
  - What it does: Fetch and merge remote changes into current branch.

- `git pull --rebase`
  - What it does: Fetch and rebase your commits on top of fetched changes.

- `git push <remote> <branch>`
  - What it does: Upload your branch to the remote repository.
  - Example: `git push origin feature/login`

- `git push -u origin <branch>`
  - What it does: Push and set the upstream tracking branch.

- `git push --force-with-lease`
  - What it does: Force push but safer — refuses if remote has new commits.

- `git push --tags`
  - What it does: Push tags to remote.

- `git remote show origin`
  - What it does: Shows remote's branches and tracking info.


## Tags

- `git tag`
  - What it does: List tags.

- `git tag v1.0.0`
  - What it does: Create a lightweight tag.

- `git tag -a v1.0.0 -m "message"`
  - What it does: Create an annotated tag with a message.

- `git show v1.0.0`
  - What it does: Show tag details.

- `git push origin v1.0.0`
  - What it does: Push a specific tag.

- `git push --tags`
  - What it does: Push all tags.


## Stash (temporary save)

- `git stash`
  - What it does: Save local changes temporarily and clean working tree.

- `git stash push -m "message"`
  - What it does: Save stash with a message.

- `git stash list`
  - What it does: List stashed changes.

- `git stash apply`
  - What it does: Apply stash but keep it in the stash list.

- `git stash pop`
  - What it does: Apply the stash and remove it from the list.

- `git stash drop <stash@{n}>`
  - What it does: Remove a specific stash entry.

- `git stash branch <branchname>`
  - What it does: Make a new branch from stash and apply it.


## Submodules

- `git submodule add <url> <path>`
  - What it does: Add another repo inside this repo as a submodule.

- `git submodule init`
  - What it does: Initialize local configuration for submodules.

- `git submodule update`
  - What it does: Fetch and checkout the submodule revisions.

- `git submodule update --remote`
  - What it does: Update submodules from their remote repositories.

- `git submodule foreach 'git pull origin main'`
  - What it does: Run a command in each submodule.


## Cherry-pick & Patches

- `git cherry-pick <commit>`
  - What it does: Apply a single commit from another branch onto current branch.

- `git format-patch <since>`
  - What it does: Create patch files for commits.

- `git apply <patchfile>`
  - What it does: Apply a patch file to working tree.


## Bisect & Debugging

- `git bisect start`
  - What it does: Start a binary search to find the commit that introduced a bug.

- `git bisect bad <bad-commit>`
  - What it does: Mark known bad commit.

- `git bisect good <good-commit>`
  - What it does: Mark known good commit.

- `git bisect reset`
  - What it does: Finish bisect and return to original HEAD.


## Search & Grep

- `git grep "pattern"`
  - What it does: Search repository files for a text pattern.

- `git log --grep="pattern"`
  - What it does: Search commit messages for a pattern.

- `git rev-list --all --grep="pattern"`
  - What it does: Search commit messages in all branches.


## Blame & Annotate

- `git blame <file>`
  - What it does: Shows which commit and author last changed each line of a file.

- `git blame -e -w <file>`
  - What it does: Show emails and ignore whitespace.


## Worktrees (multiple working directories)

- `git worktree add ../path <branch>`
  - What it does: Create another working directory for another branch.

- `git worktree remove ../path`
  - What it does: Remove a worktree.


## Sparse checkout (large repos)

- `git sparse-checkout init --cone`
  - What it does: Enable sparse checkout (only check out part of the repo).

- `git sparse-checkout set path/to/dir`
  - What it does: Pick which folders to check out.


## Hooks & Templates

- `.git/hooks/`
  - What it does: Folder where client-side hook scripts live (pre-commit, pre-push, etc.).


## Maintenance & Housekeeping

- `git gc`
  - What it does: Clean up and optimize repository storage.

- `git fsck`
  - What it does: Check repository for corruption.

- `git prune`
  - What it does: Remove unreachable objects.

- `git reflog expire --expire=now --all`
  - What it does: Expire reflog entries.


## Storing Large Files (Git LFS)

- `git lfs install`
  - What it does: Install Git Large File Storage support.

- `git lfs track "*.psd"`
  - What it does: Tell Git LFS to track matching files.

- `git lfs push --all origin main`
  - What it does: Push LFS objects to remote.


## Aliases (examples)

- `git config --global alias.st status`
  - What it does: Make `git st` run `git status`.

- `git config --global alias.co checkout`
  - What it does: Make `git co` run `git checkout`.

- `git config --global alias.lg "log --oneline --graph --decorate --all"`
  - What it does: Create a compact log view alias.


## Common Scripting & Plumbing

- `GIT_COMMITTER_DATE="..." git commit --amend --no-edit --date="..."`
  - What it does: Change commit date when amending.

- `git rev-parse HEAD`
  - What it does: Print the current commit SHA.

- `git ls-remote <repo>`
  - What it does: List remote references.


## Safety Tips (use with care)

- `git reset --hard <commit>`
  - What it does: Reset working tree and HEAD to a commit — destructive.

- `git clean -fd`
  - What it does: Remove untracked files and directories — destructive.

- `git push --force`
  - What it does: Force push and rewrite remote history — dangerous on shared branches.

- `git rebase` on public branches
  - What it does: Rewriting shared history can cause problems for others.


## Short everyday workflows

- Start new project:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <url>
git push -u origin main
