# Getting Started

Here, basic commands of the Git command-line interface are listed.

In the following chapters, you will see examples for `git` commands. 
If you want to read up on their documentation, simply use `git help <command>`.

## CLI

Git commands for setting up a repository:

- `git init`: creates a new git repo, with data stored in the `.git` directory
- `git clone <remote-source>`: downloads a repository from a remote host, either via HTTPS or SSH

Basic Git commands for regular use:

- `git status`: tells you what's going on
- `git diff <reference> <file>`: shows differences in a file between snapshots
- `git checkout <reference>`: updates HEAD to point to the referenced snapshot

Inspecting the history of a repository:

- `git log`: shows a flattened log of history
- `git log --all --graph --decorate`: visualizes history as a graph (DAG)
