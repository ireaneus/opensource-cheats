Perfect — let’s consolidate everything into a **clean, bulletproof procedure** for uploading your `ansible-project` to GitHub using **SSH**, including:

- SSH key setup & agent
- Git identity configuration
- GitHub repo linking via SSH
- Commit & push

---

# 🚀 Upload `ansible-project` to GitHub Using SSH

---

## ✅ Step 1: Configure Git Identity

Tell Git who you are (only once per system):

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

> This info will show in GitHub commits and logs.

---

## ✅ Step 2: Ensure Your SSH Key Is Loaded

If you're using a non-default SSH key (like `id_ed25519`):

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

> Confirm the key is added:
```bash
ssh-add -l
```

If you see your key listed, you're good.

---

## ✅ Step 3: Test GitHub SSH Access

```bash
ssh -T git@github.com
```

Expected result:
```bash
Hi your-username! You've successfully authenticated...
```

If it asks to confirm the GitHub host key, type `yes`.

---

## ✅ Step 4: Initialize Git in Your Project

From inside your Ansible project folder:

```bash
cd ~/Public/ansible-project

# Optional: Add a README if you haven’t yet
echo "# ansible-project" >> README.md

git init
git add .
git commit -m "Initial commit: Ansible project setup"
```

---

## ✅ Step 5: Link to GitHub Repo Using SSH

Add your GitHub repo as the `origin` using **SSH URL**:

```bash
git remote add origin git@github.com:ireaneus/ansible-project.git
```

> You can verify with:
```bash
git remote -v
```

---

## ✅ Step 6: Push to GitHub

```bash
git branch -M main
git push -u origin main
```

Done! Your Ansible project is now live on GitHub 🎉

---

## 🧠 Optional Extras

### Ignore local cache & secrets:

```bash
cat <<EOF > .gitignore
*.retry
*.log
*.swp
__pycache__/
*.pyc
.venv/
vault_pass.txt
EOF

git add .gitignore
git commit -m "Add .gitignore"
git push
```

---

## To set your identity:
```bash
git config --global user.name "John Doe"
git config --global user.email "johndoe@example.com"
```

## To set your editor:
```bash
git config --global core.editor vim
```

## To enable color:
```bash
git config --global color.ui true
```

## To stage all changes for commit:
```bash
git add --all
```

To stash changes locally, this will keep the changes in a separate changelist called stash and the working directory is cleaned. You can apply changes from the stash anytime
```bash
git stash
```

# To stash changes with a message
```bash
git stash save "message"
```

# To list all the stashed changes
```bash
git stash list
```

# To apply the most recent change and remove the stash from the stash list
```bash
git stash pop
```

To apply any stash from the list of stashes. This does not remove the stash from the stash list
```bash
git stash apply stash@{6}
```

## To commit staged changes
```bash
git commit -m "Your commit message"
```

## To edit previous commit message
```bash
git commit --amend
```

## Git commit in the past
```bash
git commit --date="`date --date='2 day ago'`"
git commit --date="Jun 13 18:30:25 IST 2015"
```
## more recent versions of Git also support --date="2 days ago" directly


## To change the date of an existing commit
```yaml
git filter-branch --env-filter \
    'if [ $GIT_COMMIT = 119f9ecf58069b265ab22f1f97d2b648faf932e0 ]
     then
         export GIT_AUTHOR_DATE="Fri Jan 2 21:38:53 2009 -0800"
         export GIT_COMMITTER_DATE="Sat May 19 01:01:01 2007 -0700"
     fi'
```

## To removed staged and working directory changes
```bash
git reset --hard
```

## To go 2 commits back
```bash
git reset --hard HEAD~2
```

## To remove untracked files
```bash
git clean -f -d
```

## To remove untracked and ignored files
```bash
git clean -f -d -x
```

## To push to the tracked master branch:
```bash
git push origin master
```

## To push to a specified repository:
```bash
git push git@github.com:username/project.git
```

## To delete the branch "branch_name"
```bash
git branch -D branch_name
```

## To make an exisiting branch track a remote branch
```bash
git branch -u upstream/foo
```

## To see who commited which line in a file
```bash
git blame filename
```

## To sync a fork with the master repo:
```bash
git remote add upstream git@github.com:name/repo.git    # Set a new repo
git remote -v                                           # Confirm new remote repo
git fetch upstream                                      # Get branches
git branch -va                                          # List local - remote branches
git checkout master                                     # Checkout local master branch
git checkout -b new_branch                              # Create and checkout a new branch
git merge upstream/master                               # Merge remote into local repo
git show 83fb499                                        # Show what a commit did.
git show 83fb499:path/fo/file.ext                       # Shows the file as it appeared at 83fb499.
git diff branch_1 branch_2                              # Check difference between branches
git log                                                 # Show all the commits
git status                                              # Show the changes from last commit
```

## Commit history of a set of files
```bash
git log --pretty=email --patch-with-stat --reverse --full-index -- Admin\*.py > Sripts.patch
```

## Import commits from another repo
```bash
git --git-dir=../some_other_repo/.git format-patch -k -1 --stdout <commit SHA> | git am -3 -k
```

## View commits that will be pushed
```bash
git log @{u}..
```

## View changes that are new on a feature branch
```bash
git log -p feature --not master
git diff master...feature
```

## Interactive rebase for the last 7 commits
```bash
git rebase -i @~7
```

## Diff files WITHOUT considering them a part of git
## This can be used to diff files that are not in a git repo!
```bash
git diff --no-index path/to/file/A path/to/file/B
```

## To pull changes while overwriting any local commits
```bash
git fetch --all
git reset --hard origin/master
```

## Update all your submodules
```bash
git submodule update --init --recursive
```

## Perform a shallow clone to only get latest commits
## (helps save data when cloning large repos)
```bash
git clone --depth 1 <remote-url>
```

## To unshallow a clone
```bash
git pull --unshallow
```

## Create a bare branch (one that has no commits on it)
```bash
git checkout --orphan branch_name
```

## Checkout a new branch from a different starting point
```bash
git checkout -b master upstream/master
```

## Remove all stale branches (ones that have been deleted on remote)
## So if you have a lot of useless branches, 
## delete them on Github and then run this
```bash
git remote prune origin
```

## The following can be used to prune all remotes at once
```bash
git remote prune $(git remote | tr '\n' ' ')
```

## Revisions can also be identified with :/text
## So, this will show the first commit that has "cool" in their message body
```bash
git show :/cool
```

## Undo parts of last commit in a specific file
```bash
git checkout -p HEAD^ -- /path/to/file
```

## Revert a commit and keep the history of the reverted change 
## as a separate revert commit
```bash 
git revert <commit SHA>
```

## Pich a commit from a branch to current branch. 
## This is different than merge as this just applies 
## a single commit from a branch to current branch
```bash
git cherry-pick <commit SHA1>
```
