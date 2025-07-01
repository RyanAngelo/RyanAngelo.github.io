---
layout: post
title:  "Node Version Manager (NVM): Essential Commands and Setup"
date:   2025-06-30 10:00:00 -0500
categories: javascript
tags: javascript, nodejs, nvm, development
author: Ryan Angelo
read_time: true
---

NVM (Node Version Manager) is an essential tool for any JavaScript developer who needs to work with multiple Node.js versions. Whether you're maintaining legacy projects, testing compatibility, or exploring new Node.js features, NVM makes switching between versions seamless.

## What is NVM?

NVM is a version manager for Node.js that allows you to install and switch between different Node.js versions on the same machine. This is particularly useful when:

- Different projects require different Node.js versions
- You need to test your code against multiple Node.js versions
- You want to try new Node.js features without affecting your system installation
- You're working with projects that have specific Node.js version requirements

### Installing Node.js Versions

```bash
# List all available Node.js versions for installation
nvm list-remote

# Install the latest LTS version
nvm install --lts

# Install a specific version
nvm install 18.17.0

# Install the latest version
nvm install node

# Install the latest version of a major release
nvm install 18
```

### Managing Installed Versions

```bash
# List all installed Node.js versions
nvm list

# Show currently active version
nvm current

# Use a specific version globally
nvm use 18.17.0

# Set a default version (used when opening new terminals)
nvm alias default 18.17.0

# Use the latest LTS version
nvm use --lts

# Use the latest version
nvm use node
```

### Project-Specific Versions

```bash
# Create a .nvmrc file in your project directory
echo "18.17.0" > .nvmrc

# Automatically use the version specified in .nvmrc
nvm use

# Install the version specified in .nvmrc if not already installed
nvm install
```

### Uninstalling and Cleaning Up

```bash
# Uninstall a specific version
nvm uninstall 16.20.0

# Remove the default alias
nvm unalias default

# Clear NVM cache
nvm cache clear
```

### Utility Commands

```bash
# Show the path to the current Node.js executable
nvm which 18.17.0

# Run a command with a specific Node.js version
nvm exec 18.17.0 node app.js

# Run npm with a specific Node.js version
nvm exec 18.17.0 npm install

# Show NVM version
nvm --version

# Get help
nvm help
```

## Working with npm and Global Packages

When you switch Node.js versions with NVM, you'll need to reinstall global packages for the new version:

```bash
# Install a package globally for the current version
npm install -g package-name

# List globally installed packages
npm list -g --depth=0

# Reinstall global packages for a new version
nvm install-latest-npm
nvm reinstall-packages-from 16.20.0
```

## Best Practices

### 1. Use .nvmrc Files

Create a `.nvmrc` file in your project root to specify the required Node.js version:

```bash
# Create .nvmrc file
echo "18.17.0" > .nvmrc

# Use the specified version
nvm use
```

### 2. Set a Default Version

Set a default Node.js version for new terminal sessions:

```bash
nvm alias default 18.17.0
```

### 3. Use LTS Versions for Production

For production applications, prefer LTS (Long Term Support) versions:

```bash
nvm install --lts
nvm use --lts
nvm alias default lts/*
```

## Troubleshooting

### Common Issues

1. **NVM command not found**: Make sure NVM is properly sourced in your shell configuration file (`.bashrc`, `.zshrc`, etc.)

2. **Permission errors**: On macOS/Linux, ensure you have the necessary permissions to install Node.js versions

3. **Global packages missing**: When switching versions, global packages need to be reinstalled

### Shell Configuration

Add these lines to your shell configuration file (`.bashrc`, `.zshrc`, etc.):

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

## Integration with Other Tools

### VS Code

VS Code can automatically detect and use the Node.js version specified in `.nvmrc`:

1. Install the "Node Version Manager" extension
2. VS Code will automatically switch to the correct Node.js version when opening projects with `.nvmrc` files

### CI/CD Pipelines

In CI/CD environments, you can use NVM to ensure consistent Node.js versions:

```yaml
# Example GitHub Actions workflow
- name: Setup Node.js
  uses: actions/setup-node@v3
  with:
    node-version-file: '.nvmrc'
```