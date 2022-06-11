# The basics
### Checkout new branch
`$ git checkout -b [branch_name]`

### Push branch to remote repo (aka origin) / create a PR
`$ git push origin [branch_name]`

# Checkout a remote branch
### Why would I want to do this?
Someone on the team pushes a branch to the remote shared repo with `$ git push origin [branch_name]` and you want to pull that branch onto your local machine

### How do I do it (Git version > 2.23)?
1) Start by fetching from the remote repo (including branches): 
```bash
$ git fetch
``` 
2) [Optional] List the branches available for checkout:
```bash
$ git branch -v -a
```
3) Checkout a remote branch
```bash
$ git switch [branch_name]
```

### How do I do it with an older version of Git? 
1) Checkout the remote branch
```bash
$ git checkout [branch_name]
```

* [StackOverflow link](https://stackoverflow.com/questions/1783405/how-do-i-check-out-a-remote-git-branch)


# Checkout old commit and make it a new commit
### Why would I want to do this?
You suspect some recent commits may have introduced a bug and want the repo to revert to the state it was in prior to those commits. In other words, if you commit history looks like:
A-B-C-D-E
        ^
        current commit

you want it to become:
A-B-C-D-E-F
          ^ 
          current commit (where F is identical to C)

### What's the non-git-centric way to do this? 
Delete, edit files manually to get back to the state of the old commit

### What's the git approach? 
```bash
$ git rm -r .
$ git checkout [SHA(see below)] .
$ git commit -m "[message]" 
```

* [StackOverflow link](https://stackoverflow.com/questions/3380805/checkout-old-commit-and-make-it-a-new-commit)
* Git SHA (simple hashing algorithm): it's the alpha numeric code that identifies a commit. Run `git log` or `git log --oneline` from within a repo you've worked on to see

# Reversing Changes
## Accidental Commit
### What would I want to do this?
You want to undo JUST the last commit for whatever reason
- Realized after the commit that you were on the wrong branch.
- Realized that you accidentally added some incorrect files

### Show me the money! What are the git commands?
```bash
$ git reset --soft HEAD~1
```
This will "uncommit" the most resent commit, but it WILL preserve all of the changes within your files still. BUT it will leave git with all of the those files in the staging area still. Read on to unstage files.

## Unstage ALL staged files in git
### What would I want to do this?
You are undoing an accidental commit, or you want to remove all staged files and start again
- Realized that you accidentally added some incorrect files

### Show me the money! What are the git commands?
```bash
$ git reset
```