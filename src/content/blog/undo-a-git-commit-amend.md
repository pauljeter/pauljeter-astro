---
title: "Undo a git commit --amend"
description: ""
pubDate: 2014-10-28
heroImage: '/images/git.jpg'
categories: 
  - "workflow-tools"
tags: 
  - "git"
  - "version-control"
  - "web-development"
  - "workflow-tools-2"
---

I recently executed a `git commit --amend` by accident, committing my changes to a commit that was behind my co-worker's commit. This commit should have been separate, allowing me to pull the latest from the remote repository and rebase, before pushing and merging my changes. This caused several merge issues that were unnecessary. Luckily, there was a simple solution to remedy my mistake.

```
# Move the current head so that it's pointing at the old commit
# Leave the index intact for redoing the commit
git reset --soft HEAD@{1}

# commit the current tree using the commit details of the previous
# HEAD commit. (Note that HEAD@{1} is pointing somewhere different from the
# previous command. It's now pointing at the erroneously amended commit.)
git commit -C HEAD@{1}
```

The solution involved creating a new commit with the same details as the current `HEAD` commit, but with the parent as the previous version of `HEAD`. `git reset --soft` will move the branch pointer so that the next commit happens on top of a different commit from where the current branch head is now.
