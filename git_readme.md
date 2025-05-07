
# Git Commands Reference Guide

## Table of Contents
1. [Repository Setup](#repository-setup)
2. [Basic Configuration](#basic-configuration)
3. [File Operations](#file-operations)
4. [Staging and Committing](#staging-and-committing)
5. [Branching](#branching)
6. [History and Logs](#history-and-logs)
7. [Remote Operations](#remote-operations)
8. [Workshop Example](#workshop-example)

## Repository Setup
```bash
# Create a new Git repository
git init

# Create and enter project directory
mkdir git-github-workshop
cd git-github-workshop
```

## Basic Configuration
```bash
# Set global username
git config --global user.name "YourUsername"

# Set global email
git config --global user.email "your.email@example.com"
```

## File Operations
```bash
# Create a new file
touch filename.txt

# Remove a file
rm filename.txt

# Restore a deleted file from Git
git restore filename.txt

# List all files (including hidden)
ls -a
```

## Staging and Committing
```bash
# Check repository status
git status

# Add file to staging area
git add filename.txt

# Add all files to staging area
git add .

# Remove file from staging area
git rm --cached filename.txt

# Commit changes
git commit -m "your commit message"
```

## Branching
```bash
# Create and switch to new branch
git checkout -b branch_name

# Switch between branches
git checkout branch_name

# List all branches
git branch
```

## History and Logs
```bash
# View commit history
git log

# View simplified commit history
git log --oneline
```

## Remote Operations
```bash
# Add remote repository
git remote add origin https://github.com/username/repository.git

# View remote repositories
git remote -v

# Update remote URL
git remote set-url origin https://github.com/username/repository.git

# Push changes to remote
git push origin branch_name

# Pull changes from remote
git pull origin branch_name
```

## Workshop Example
Here's a practical example from a Git workshop:

```bash
# Setup repository
mkdir git-github-workshop
cd git-github-workshop
git init
ls -a

# Create and manage files
git status
git add testing.py
git status
git rm --cached testing.py
git add testing.py
git commit -m "added testing.py file"

# File recovery example
rm testing.py
git restore testing.py

# Remote repository operations
git remote add origin https://github.com/username/git-github-workshop.git
git remote -v
git push origin master

# Update remote URL if needed
git remote set-url origin https://github.com/username/git-github-workshop

# Synchronize changes
git add testing.py
git commit -m "update testing.py"
git push origin master
git pull origin master
```

### Common Issues and Solutions
1. If push fails, try pulling first: `git pull origin master`
2. For authentication issues, ensure your remote URL is correct
3. Always check status with `git status` before operations
4. Use `git restore` to recover deleted files

### Best Practices
1. Commit often with clear messages
2. Pull before pushing to avoid conflicts
3. Use meaningful branch names
4. Keep your local repository updated
5. Verify your remote URL configuration

Remember to replace `username` and `repository` in remote URLs with your actual GitHub username and repository name.
