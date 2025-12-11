# Git Reference

## Content

## Installing Git

### On Linux 
```bash
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install git
```
## Configuration Commands
Configure global username, email, and password
```bash
$ git config --global user.name "my_username"
$ git config --global user.email "my_email@email"
$ git config --global user.password "my_password"
```
Set the default branch name
```bash
$ git config --global init.default branch <branchname>
```
Show detail of current git configuration
```bash
$ git config -l
```
Cache the record on computer to remember the current git configuration 
```bash
$ git config --global credential.helper cache
```
Delete cache record of git configuration 
```bash
$ git config --global --unset credential.helper
$ git config --system --unset credential.helper
```

## Basic Commands
Initialize current working directory as a git repository. This will create a hidden folder ".git" indicating git repository is initialized