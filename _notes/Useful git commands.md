---
season: spring
tags:
  - tools
  - programming
---
# Git unadd
The command to remove a staged file (i.e. added with `git add`) is `git reset`. I always forget it so I created an alias to run `git unadd`: in `~/.gitconfig`, add the lines:
```
[alias]
    unadd = reset
```
# Show changed files' names

List names of changed files -- like `git diff`, but only show the changed files' names :

Use the option `--name-only`, ex:

```
git diff HEAD~1 --name-only
```

# Undo amend 

Move the current head so that it's pointing at the old commit. Leave the index intact for redoing the commit. `HEAD@{1}` gives you "the commit that HEAD pointed at before it was moved to where it currently points at". Note that this is xdifferent from `HEAD~1`, which gives you "the commit that is the parent node of the commit that HEAD is currently pointing to."

```
git reset --soft HEAD@{1}
```

Commit the current tree using the commit details of the previous HEAD commit. (Note that `HEAD@{1}` is pointing somewhere different from the previous command. It's now pointing at the erroneously amended commit.)

```
git commit -C HEAD@{1}
```

[source](https://stackoverflow.com/a/1459264)

# Undo last commit but keep changes in staging

When you want to reset the local git repository's state to just before a commit, without losing the changes. Caution: if the commit was pushed, this will create a conflict between the local and remote versions.

```
git reset --soft HEAD~1
```

[source](https://stackoverflow.com/questions/19859486/how-to-un-commit-last-un-pushed-git-commit-without-losing-the-changes)

# Make branch point to specific commit

You can make `master` point at `1258f0d0aae` this way:

```
git checkout master
git reset --hard 1258f0d0aae
```

But you have to be careful about doing this. It may well rewrite the history of that branch. That would create problems if you have published it and other people are working on the branch.

Also, the `git reset --hard` command will throw away any uncommitted changes (i.e. those just in your working tree or the index).

You can also force an update to a branch with:

```
git branch -f master 1258f0d0aae
```

... but git won't let you do that if you're on `master` at the time.

[source](https://stackoverflow.com/a/7310222/8725263)