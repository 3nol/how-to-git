# Overview

Git is a version control system (VCS).

## What is a VCS?

Version control systems are tools used to track changes in source code
(or other collections of files and folders). As the name implies, these tools
help to maintain a history of changes.

VCSs track changes to a folder and its contents in a series of _snapshots_, where
each snapshot encapsulates the entire state of files/folders within a directory.
VCSs also maintain metadata like who created each snapshot, messages associated
with each snapshot, and so on.

### Why is version control useful?

Even when you're working by yourself, it can let you look at old snapshots of
a project, keep a log of why certain changes were made, work on parallel branches
of development, and much more. When working with others, it's an invaluable tool
for seeing what other people have changed, as well as resolving conflicts in
parallel development.

Modern VCSs also let you easily answer questions like:

- Who wrote this module?
- When was this particular line of this particular file edited? By whom? Why
  was it edited?
- Over the last 1000 revisions, when/why did a particular unit test stop
working?
- Who is to blame for that nasty bug?

While other VCSs exist, **Git** is the de facto standard for version control.
However, working with Git can be frustrating at times.
This [XKCD comic](https://xkcd.com/1597/) captures Git's reputation:

<div style="text-align: center;">
<img src="https://imgs.xkcd.com/comics/git.png" width="300px">
</div>

Starting with Git's command-line interface can lead to a lot of confusion.
It's possible to memorize a handful of commands and think of them as magic
incantations, and follow the approach in the comic above whenever anything goes
wrong.

While Git admittedly has an ugly interface, its underlying design and ideas are
beautiful. While an ugly interface has to be _memorized_, a beautiful design
can be _understood_. Hence, this tutorial covers a bottom-up explanation of Git,
starting with its data model and later covering the command-line interface (CLI).

## How does Git do versioning?

There are many ad-hoc approaches you could take to version control. Git has a
well-thought-out model that enables all the nice features of version control.

### Snapshots

Git models the history of a collection of files and folders within some
top-level directory as a series of snapshots. In Git terminology, a file is
called a _blob_, and it's just a bunch of bytes. A directory is called a
_tree_, and it contains other blobs or trees. A snapshot is the top-level
tree that is being tracked. For example, we might have a tree as follows:

```
<root> (tree)
|
+- foo (tree)
|  |
|  + bar.txt (blob, contents = "hello world")
|
+- baz.txt (blob, contents = "git is wonderful")
```

The top-level tree contains two elements, a tree "foo" (that itself contains
one element, a blob "bar.txt"), and a blob "baz.txt".

#### Modeling history

In Git, a history is a directed acyclic graph (DAG) of snapshots. That may
sound like a fancy math word, but don't be intimidated. All this means is that
each snapshot in Git refers to a set of "parents", the snapshots that preceded
it. It's a set of parents rather than a single parent because a snapshot might
descend from multiple parents, for example, due to combining changes from
multiple sources.

### References

All snapshots are identified by their _hash codes_. That's inconvenient,
because humans aren't good at remembering strings of 40 hexadecimal characters.

Git's solution to this problem is human-readable names for hashes called
_references_. References are pointers to commits. Unlike hashes, which are
immutable, references are mutable (can be updated to point to a new snapshot).
For example, the `master` reference usually points to the latest
snapshot in the main branch of development.

One detail is that we often want a notion of where we currently are in the
history, so that when we make a new snapshot, we know what it is relative to.
In Git, that "where we currently are" is a special reference called `HEAD`.

### Repositories

Finally, we can define what (roughly) is a Git _repository_. It is the data
`objects` and `references`. Git stores the objects and references on the disk.
They are bundled into a repository.

All `git` commands map to some manipulation of the snapshot DAG by adding
objects and updating references. Whenever you're typing in a command, think
about what manipulation you are making to the underlying graph data structure.
