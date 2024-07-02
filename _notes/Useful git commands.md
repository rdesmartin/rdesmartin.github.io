---
season: spring
tags:
  - tools
  - programming
---

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