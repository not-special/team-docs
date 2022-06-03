# The basics
### Checkout new branch
`$ git checkout -b [branch_name]`

### Push branch to remote repo (aka origin) / create a PR
`$ git push origin [branch_name]`


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