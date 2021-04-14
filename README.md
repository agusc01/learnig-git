# The three more important things: 
- git add
- git commit
- git push


<a href="https://git-scm.com/docs">references for know how to use GIT commands</a><br>
<a href="https://git-scm.com/docs/git#_git_commands">complete documentation about GIT commands</a>

<br>

# How can you be ?
- 0 : clean
- 1 : untracked/unstaged
- 2 : staged
- 3 : commit
- 4 : remote (push)
 

**Cheatsheet:**<br>

*Forward:*<br>
git add \<file><br>
git commit -m "Message for this commit"<br>
git push -u \<remote branch name> \<local branch name>

*Backward:*<br>
git reset --soft HEAD~ 1 (from commit to staged) [3->2]<br>
git reset --mixed HEAD ~1 (from commit to untracked) [3->1]<br>
**DANGER**: git reset --hard HEAD ~1 (from commit to clean) [3->0]<br>
git restore --staged \<file> (from staged to untracked)
git restore \<file>  (from untracked to clean, file previously at least one commit) [1->0]<br>

## List of commands seen in this file
- <a href="#Basic-section">git config</a>
- <a href="#Start-a-local-repository-section">git int</a>
- <a href="#Start-a-local-repository-section">git remote</a>
- <a href="#Start-a-remote-repository-section">git clone</a>
- <a href="#Add-section">git add | stage</a>
- <a href="#Check-section">git status</a>
- <a href="#Commit-section">git commit</a>
- <a href="#Branch-section">git branch</a>
- <a href="#Branch-section">git checkout</a>
- <a href="#Merge-section">git merge</a>
- <a href="#Log-section">git log</a>
- <a href="#Diff-section">git diff</a>
- <a href="#Stash-section">git stash</a>
- <a href="#Tag-section">git tag</a>
- <a href="#Download-section">git pull</a>
- <a href="#Download-section">git fetch</a>
- <a href="#Push-section">git push</a>
- <a href="#Blame-section">git blame</a>
- <a href="#Reset-section">git reset</a>
- <a href="#Rebase-section">git rebaes</a>
- <a href="#Cherry-pick-section">git cherry-pick</a>


<br>

## Basic section

To configure your user name & email (globally: global | localy: local [specific repository])

    git config --global user.name "John Doe"
    git config --global user.name "johnDoe@mail.com"

To configure global|local alias

    git config --global alias.lo 'log --online'
    git config --local alias.lo 'log --online'

To view ALL global|local configurations

    git config --global --list
    git config --local --list

To remove a configuration. For example:

    git config --global --unset user.name
    git config --global --unset alias.lo

<br>

## Start a local repository section

To create a local repository (only once per repository)

    git init

To add a new URL from remote repository 

    git remote add <remote branch name> <URL:git>
    
To set up the URL from remote repository 

    git remote set-url <remote branch name> <URL:git>

<br>

## Start a remote repository section

To clone a repository

    git clone <ULR:git>

To clone a repository & change the folder name

    git clone <URL:git> "folderName"

<br>

## Add section

To add files|folders to stage area

    git add <file|folder>
    git stage <file|folder>

To add ALL files|folders to stage area

    git add .
    git add --all
    git stage .
    git stage --all
<br>

## Check section

To know the remote branch name (with -v to know the URL remote repository)

    git remote
    git remote -v

To view the files|folders status (with -s give the ouput in the short-format)

    git status
    git status -s

<br>

## Commit section

To create a commit (use your default-inferface)

    git commit

To create a commit & put a message

    git commit -m "your message, no more than 52 letters"

To create add ALL files to stage area & commit with a message

    git commit -a -m "your message, no more than 52 letters"

To redo the last commit

    git commit --amend 
<br>

## Branch section

To create a new branch where you are (pointer HEAD), to a specific commit, to a specific stash (n: natural number)

    git branch <branch name>
    git branch <branch name> HEAD~n
    git branch <branch name> <hash commit>
    git branch <branch name> stash@{n}


To list ALL local braches

    git branch

To list ALL remote branches

    git branch -r

To list ALL local | remote branches

    git branch -a

To rename a branch

    git branch -m <old branch name> <new branch name>

To move between branches or move between commits

    git checkout <branch name>
    git checkout <hash commit>

To create & move a new branch

    git checkout -b <branch name>

To delete a branch

    git branch -d <branch name>

## Merge section

To merge two branches. You must be in the branch you want & put the name of the branch that will come to merge

    git merge <branch name>
<br>

## Log section

To view the commit history (give you the output in the long-format)

    git log

To view the commit history (give you the short-format)

    git log --oneline

To view the last five commit in short-format

    git log --oneline -n 5

To view ALL commit history (even pointers from othera branches pointers)

    git log --all

To view commit history in graph format

    git log --graph

To know how many lines were inserted or removed

    git log --stat

Look for differences that change the number of occurrences of the specified string (i.e. addition/deletion) in a file. Intended for the scripter’s use

    git log -S <string>

<br>

## Diff section

To view the differences between two commits (you can use the head pointer as reference)

    git diff <first hash commit> <second hash commit>

**Note: "git diff" is equals to "git diff HEAD~1 HEAD"** 
<br><br>

## Stash section
-. Stash works as FIFO (first in first out)

To create a stash

    git stash

To view all stashes

    git stash list

To go back to the last stash or a specific stash 

    git stash apply
    git stash apply stash@{n}

To delete the last stash or a specific stash 

    git stash drop
    git stash drop stash@{n}

To go back to the last stash & delete it at same time or a specific stash 

    git stash pop
    git stash pop stash@{n}

To create a stash with a message

    git stash save "your message, no more than 52 letters"

To get information about how many files were modified &| created, how many lines were inserted or removed

    git stash show stash@{n}

To view a differences to a specific stash

    git stash -p stash{n}

To delete ALL stashes

    git stash clear
<br>

## Tag section

To create a tag where is the "HEAD"

    git tag -a <tag name> 

To create a tag to a specific commit

    git tag -a <tag name> <hash commit>

To create a Tag with a message (like a commit)

    git tag -a <tag name> -m "your message, no more than 52 letters"

To list all tags 

    git tag

To list specific tags **(filter tags, * is a special character)**

    git tag -l "v.0.*"

To delet a tag **(don't need to stay with the HEAD pointer)**

    git tag -d <tag name> 

### Important: Tags don't go to the remote repository automatically (remember "origin" is the default remote branch name). For this action do something like :

    git push <remote branch name> <tag name>

To send all tags to the remote repository 

    git push <remote branch name> --tags
<br>

## Download section

To download updates from the remote repository & do a merge automatically

    git pull <remote branch name> <local branch name>

*note: pull is equals fetch & merge at the same time*

To download updates from the remote repository & **don't** merge automatically

    git fetch <remote branch name> <local branch name>
<br>

## Push section

To send your work to the remote repository

    git push -u <remote branch name> <local branch name>
<br>

## Blame section

To know who write the file (find the commit author) & in a specific lines (4 to 9)

    git blame <file>
    git blame -L 4,9 <file>

To know who write the file. (view full hash commit)

    git blame -l <file>
<br>

## Reset section

<br>

## Rebase section

<br>

## Cherry-pick section