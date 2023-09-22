# Getting Started

Here, you find some basic commands of the Git command-line interface.

In the following chapters, you will see more examples for `git` commands. 
If you want to read up on their documentation, simply use `git help <command>`.

## CLI

Git commands for setting up a repository:

- `git init` \
    Creates a new repository in the current directory, 
    with data stored in the (hidden) `.git` directory.
- `git clone <remote-source>` \
    Downloads a repository from a remote host, either via HTTPS or via SSH.

Basic Git commands for regular use:

- `git status` \
    Tells you what's going on.
- `git diff <reference> <path>` \
    Shows differences in a file path between snapshots.
- `git checkout <reference>` \
    Updates `HEAD` (current snapshot position) to point to the given reference.

Inspecting the history of a repository:

- `git log` \
    Shows a flattened log of history of commits, incl. their messages.
- `git log --all --graph --decorate` \
    Visualizes history as a graph (DAG).
