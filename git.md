
## ... clone existing repository and do some changes
```shell
git clone git@github.com:krudisar/git@github.com:krudisar/astros-v1.git
echo "# appA" >> newfile.md
git add newline.md
git commit -m "first commit"
git push

# then delete the file 'newfile.md' in GitHub UI

# check if the newfile.md is still available locally
astros-v1 % ls 

# sync the repository from the GitHub using 'git pull'
astros-v1 % git pull

remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 2 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (2/2), 587 bytes | 195.00 KiB/s, done.
From github.com:krudisar/astros-v1
   21dc365..7b8e72c  master     -> origin/master
Updating 21dc365..7b8e72c
Fast-forward
 newfile.md | 1 -
 1 file changed, 1 deletion(-)
 delete mode 100644 newfile.md      # <-----------
```
## How to add .gitignore file to prevent copying certain files to remote repository

1. Place .gitignore file to the root repository folder
2. Add files names

```shell
.DS_Store
*.txt
!readme.txt
```

the **.gitignore** file above will prevent file .DS_Store, any file with .txt extension to be copied to remote repository (GitLab)
the only exception is file with name readme.txt (the ! at the beginning of the line says 'this is an exception', copy the file

### What if a file already exists in remote repository (GitLab) ?

**.gitignore** won't ignore a file that's already in your repository. You have to first remove the file for your repository. 
You can remove a file from the repository without deleting the actual file with **git rm --cached**.


## How to change Terminal prompt to show git branch (Linux)
In case of new repo created locally, the current branch shows up (git branch) after first commit
```shell
curl -o ~/.git-prompt.sh https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
echo 'source ~/.git-prompt.sh' >> ~/.bashrc
```

## How to change author's name & email
```shell
git commit --amend --reset-author
```

## How to add and commit all changes (but NOT in NEW files)
```shell
git commit -am  "<commit message>"
git push
```

## How to add and commit all changes done in all files (including NEW files)
```shell
git add --all && git commit -m "comment"
git push
```

> TIP: !!! How to change a Git commit messages after a push -> https://www.educative.io/answers/how-to-change-a-git-commit-message-after-a-push

## … or create a new repository on the command line
```shell
echo "# appA" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:krudisar/appA.git
git push -u origin main
```


## … or push an existing repository from the command line
```shell
git remote add origin git@github.com:krudisar/appA.git
git branch -M main
git push -u origin main
```


## … show commits and list differences between 2 commits
```shell
# either this way ...
git log --reflog
# ... or this way
git log --all --oneline

output:

7b8e72c (HEAD -> master, origin/master, origin/HEAD) Delete newfile.md
21dc365 added newfile.md
5cc82aa (origin/dependabot/pip/certifi-2022.12.7) Bump certifi from 2019.3.9 to 2022.12.7
85c9d4a (origin/dependabot/pip/rsa-4.7) Bump rsa from 4.0 to 4.7
0761c34 (origin/dependabot/pip/httplib2-0.19.0) Bump httplib2 from 0.12.1 to 0.19.0
c698ef9 (origin/dependabot/pip/typed-ast-1.3.2) Bump typed-ast from 1.3.1 to 1.3.2
8f854b5 (origin/dependabot/pip/werkzeug-0.15.3) Bump werkzeug from 0.15.1 to 0.15.3
43d14f9 Update app.py
b211bab fixed image url caching
075d376 commit
1f33395 commit
449f5aa commit
0002837 added build file for Docker
dd1a2ff commit
5637073 commit
c677451 Initial Commit
8a35324 Initial Commit

# show what has changed between these two commits
git diff 8a35324..43d14f9

# in case only one commit was done, you can list the changes (against original version -> HEAD)

# get commit_id
git log --reflog

# show changes in the first commit
git diff commit_id


```
