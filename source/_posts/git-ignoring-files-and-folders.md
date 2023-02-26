---
title: Git - Ignoring files and folders
date: 2023-02-26
---

> The idea here is not to have the files or folders show up in the change list in the IDE.

## Ignoring untracked files and folders

1. Versioned configuration:
    `<repoFolder>/.gitignore`

2. Not versioned configuration:
    `<repoFolder>/.git/info/exclude`


## Ignoring tracked files

```bash
git update-index --assume-unchanged filepath
git update-index --no-assume-unchanged filepath
```
