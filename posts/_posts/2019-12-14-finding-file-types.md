---
layout: post
title:  "Finding all file types in a directory"
date:   2019-12-14 16:00:00 -0400
categories: unix
tags: unix
author: Ryan Angelo
---

Found this cool [stackoverflow post](https://stackoverflow.com/questions/1842254/how-can-i-find-all-of-the-distinct-file-extensions-in-a-folder-hierarchy) that describes how to find all of the file types that exist in a directory:

```find . -type f | perl -ne 'print $1 if m/\.([^.\/]+)$/' | sort -u```