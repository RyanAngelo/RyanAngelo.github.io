---
layout: post
title:  "Helpful Git Metrics Information"
date:   2019-08-28 16:42:29 -0400
categories: git
tags: linux, unix, git
author: Ryan Angelo
---

The following snippets help obtain information about the number of lines of code that were changed in a git repository.

### Get commit information between two dates

```sh
git log --oneline --stat --after="2019-05-28" --before="2019-08-28" --pretty="@%h" | grep -v \| |  tr "\n" " "  |  tr "@" "\n"
```

### Get the lines of code that were changed between two commits or two tags

```sh
git diff --shortstat <taga> <tagb>
```

### Get the number of lines of code (ESLOC) for a repository for a given file type

```sh
git ls-files | grep -P ".*\.filetype$" | xargs wc -l  
```
where filetype is the type of file whose lines you want to count.
