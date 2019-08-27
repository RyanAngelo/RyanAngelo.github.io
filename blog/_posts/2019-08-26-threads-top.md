---
layout: post
title:  "Show a list of processes sorted by number of threads"
date:   2019-08-26 16:42:29 -0400
categories: linux
tags: linux, unix
author: Ryan Angelo
---

{% include nav.html %}

The following allows for the top 10 processes that are using the most threads. Threads are described by the NLWP (Number of Lightweight Processes) value.

```sh
watch -n 1 'ps -eo nlwp,pid,args --sort -nlwp | head'
```

{% include nav.html %}