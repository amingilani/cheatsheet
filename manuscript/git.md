# Git

Git is the open source distributed version control system that facilitates GitHub activities on your laptop or
desktop. This cheat sheet summarizes commonly used Git command line instructions for quick reference.

## Git CLI

```bash
# Configuration
$ git config --global user.name "John Smith" # use this name for commits
$ git config --global user.email "john@example.com" # use this email for commits
$ git config --global color.ui auto # enable colored output

# Creating repositories
$ git init . # Initialize a repository in this folder
$ git init myproject # Create a new folder and initialize a repo
$ git clone git@git@github.com:amingilani/cheatsheet.git # create a local clone

# Making changes
$ git status # review changes since last commit

$ git add . # add all files in current directory to staging
$ git add hello.txt # add the hello.txt file to staging

$ git reset . # Unstage all files in the current directory, but preserve changes
$ git reset hello.txt # Unstage hello.txt, but preserve changes

$ git diff # show file differences that are not yet staged
$ git diff --staged # show staged file differences

$ git commit -m "Add hello.txt" # Commit the staged files with this message
$ git commit # Commit the staged files and open the editor to input the message


# Branches
$ git branch # list all local branches in the current repository

$ git branch feature # create a new branch called `feature`
$ git checkout feature # switch the `feature` branch
$ git checkout -b feature # create a new branch called feature and switch to it

$ git merge feature # merge the feature branch's changes into the current branch
$ git merge gilani/master # merge remote gilani's master branch
$ git branch -d feature # deletes the feature branch

# Working with remotes

git remote # show all the remote repositories associated with this project
git remote -v # show the remotes verbosely, i.e with their urls

$ git remote add cheatsheet git@github.com:amingilani/cheatsheet.git # add a remote
$ git remote rename cheatsheet upstream # rename the remote to gilani
$ git remote rm gilani # remove the remote named gilani
$ git remote set-url origin git@github.com:amingilani/cheatsheet.git # change remote url

$ git push origin master # push all local changes to remote repository's master
$ git push -u origin master # push local changes to remote and set it as default
$ git push # push local changes to default remote
$ git push -f # force a push even if repo history is different from remote

$ git fetch gilani # download / update the history from the gilani remote

$ git pull origin master # pull all local changes from remote repository's master
$ git pull -u origin master # pull local changes from remote and set it as default
$ git pull # pull local changes from default remote
$ git pull -f # force a pull even if repo history is different from remote

# File management
$ git rm hello.txt # delete hello.txt and stage deletion
$ git rm --cached hello.txt # remove from git but preserve the file locally
$ git rm -rf hello/ # delete the hello directory and stage deletion

$ git mv hello.txt goodbye.txt # rename the file and stage it

# Save work in progress
$ git stash # temporarily store all modifications to tracked files
$ git stash list # lists all stashed changes
$ git stash pop # restore last stashed files
$ git stash drop # delete the latest stash

# Undoing changes
$ git reset 69f2382 # checkout all the files at 69f2382 and make a new commit
$ git reset --hard 69f2382 # rewind to commit 69f2382, and delete all commits since

# Review history
$ git log # list commits for the current branch
$ git log --follow hello.txt # lists commits that modified or renamed hello.txt
$ git diff master...feature # shows content diff between master and feature
$ git show 69f2382 # show details of commit 69f2382

$ git shortlog -n --after="7 days ago" # show commit messages by user for 7 days
```

## gitignore

Files specified in `.gitignore` are not commited by git to the project repo.
For quickly putting together a starter gitignore visit [gitignore.io](https://gitignore.io)

Gitignore files created in subdirectories will override the gitignore in the
project root.


Pattern Format:

The following is sourced from [git-scm](https://git-scm.com/docs/gitignore)

* A blank line matches no files, so it can serve as a separator for readability.
* A line starting with # serves as a comment. Put a backslash ("\") in front of the first hash for patterns that begin with a hash.
* Trailing spaces are ignored unless they are quoted with backslash ("\").
* An optional prefix "!" which negates the pattern; any matching file excluded by a previous pattern will become included again. It is not possible to re-include a file if a parent directory of that file is excluded. Git doesn’t list excluded directories for performance reasons, so any patterns on contained files have no effect, no matter where they are defined. Put a backslash ("\") in front of the first "!" for patterns that begin with a literal "!", for example, "\!important!.txt".
* If the pattern ends with a slash, it is removed for the purpose of the following description, but it would only find a match with a directory. In other words, foo/ will match a directory foo and paths underneath it, but will not match a regular file or a symbolic link foo (this is consistent with the way how pathspec works in general in Git).
* If the pattern does not contain a slash /, Git treats it as a shell glob pattern and checks for a match against the pathname relative to the location of the .gitignore file (relative to the toplevel of the work tree if not from a .gitignore file).
* Otherwise, Git treats the pattern as a shell glob suitable for consumption by fnmatch(3) with the FNM_PATHNAME flag: wildcards in the pattern will not match a / in the pathname. For example, "Documentation/*.html" matches "Documentation/git.html" but not "Documentation/ppc/ppc.html" or "tools/perf/Documentation/perf.html".
* A leading slash matches the beginning of the pathname. For example, "/*.c" matches "cat-file.c" but not "mozilla-sha1/sha1.c".

Two consecutive asterisks ("**") in patterns matched against full pathname may have special meaning:

* A leading "\*\*" followed by a slash means match in all directories. For example, "\*\*/foo" matches file or directory "foo" anywhere, the same as pattern "foo". "\*\*/foo/bar" matches file or directory "bar" anywhere that is directly under directory "foo".
* A trailing "/\*\*" matches everything inside. For example, "abc/\*\*" matches all files inside directory "abc", relative to the location of the .gitignore file, with infinite depth.
* A slash followed by two consecutive asterisks then a slash matches zero or more directories. For example, "a/\*\*/b" matches "a/b", "a/x/b", "a/x/y/b" and so on.
* Other consecutive asterisks are considered invalid.
