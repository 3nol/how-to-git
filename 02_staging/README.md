# Staging

This is another concept that's orthogonal to the data model, but it's a part of
the interface to create commits.

One way you might imagine implementing snapshotting is to have a "create snapshot"
command that creates a new snapshot based on the current state of the working
directory. Some version control tools work like this, but not Git.

We want clean snapshots, and it might not always be ideal to make a snapshot from
the current state. For example, imagine a scenario where you've implemented two
separate features, and you want to create two separate commits, where the first
introduces the first feature, and the next introduces the second feature.

Git accommodates such scenarios by allowing you to specify which modifications
should be included in the next snapshot through a mechanism called the _staging
area_. Unstaged changes will not be included in your commits.

## CLI

There are many [GUI clients](https://git-scm.com/downloads/guis) out there for Git.
They might be helpful when having lots of changes to compare and decide on.

But for now, we will focus on the command-line interface which provides you with
all the controls you need. To check which files are currently only changed, which
are staged and which are committed, you can use `git status`.

### Adding to staging area

The following command is used push files into the staging area:

- `git add <path>`

You can specify one or multiple files and even use wildcards to add multiple files
at once. For example, when doing Java development, you can use `git add "*.java"`.

### Removing from staging area

Use this command for removing a one or multiple files from the staging area:

- `git restore --staged <path>` \
    Does not change the content at the path, but unstages it.

### Removing changes completely (from disk)

Sometimes you might want to discard changes completely. These commands do that:

- `git checkout -- <path>` \
    Discards all non-staged changes.
- `git rm [--cached] <path>` \
    With this command, you can remove changes that were already staged or committed.
    Specifying the `--cached` flag does not remove the files from disk, only from Git.
