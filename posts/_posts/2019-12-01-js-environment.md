---
layout: post
title:  "Setting up a Quick JavaScript Environment"
date:   2019-12-01 16:00:00 -0400
categories: js
tags: js, macOS
author: Ryan Angelo
---

I wanted to spend some time getting more comfortable with JavaScript and experiment with some 3D rendering frameworks, but needed to first work on getting a development environment setup.

### NPM or Yarn?

I had experience using NPM and because of some of the security issues that NPM has been suffering from, I thought I would get some exposure to [Yarn](https://yarnpkg.com/en/), which is an alternative to NPM and has some interesting features. It caches every package that it downloads, which maximizes resource utilization and uses checksums for verifying the integrity of installed packages.

I use macOS for development, and tend to use the [Homebrew Package Manager](https://brew.sh) whenever possible, making installing yarn as simple as

```bash
brew install yarn
```

### Development Server

Next I wanted a quick and easy way of testing the JavaScript that I was working on. The experimentation that I want to do, particularly with [three.js](https://threejs.org) would only be simple JavaScript, HTML and CSS; so I decided to just use the http.server included in Python. 
Starting up the Python HTTP server is simply a matter of running

```bash
python3 -m http.server
```

This will serve content from the current directory on port 8000. You can also bind it to a specific address with --bind.

The http.server has minimal security restrictions, so it should not be used for production.

### Browserify

Being able to manage packages that were installed through Yarn and easily import them and distribute them made me look into [Browserify](https://github.com/browserify/browserify) which looks at all the require() calls that you have and builds up a bundle that you can serve in a single script tag.

I installed this globally with Yarn, because it would not be tied to a specific project.

```bash
yarn global add browserify
```
