# Commits

Git calls snapshots _commits_. Visualizing a commit history might look
something like this:

```
o <-- o <-- o <-- o
            ^
             \
              --- o <-- o
```

In the ASCII art above, the `o`'s correspond to individual commits (snapshots).
The arrows point to the parent of each commit (it's a "comes before" relation,
not "comes after"). After the third commit, the history branches into two
separate branches. This might correspond to, for example, two separate features
being developed in parallel, independently from each other. In the future,
these branches may be merged to create a new snapshot that incorporates both of
the features, producing a new history that looks like this, with the newly
created merge commit shown in <strong><font color="green">green</font></strong>.

<pre class="highlight">
<code>
o <-- o <-- o <-- o <---- <strong><font color="green">o</font></strong>
            ^            /
             \          v
              --- o <-- o
</code>
</pre>

Commits in Git are immutable. This doesn't mean that mistakes can't be corrected. 
However, it's just that edits to the commit history are actually creating entirely 
new commits, and references are updated to point to the new ones.

## Structure of a snapshot 

It may be instructive to see Git's data model written down in Python-like pseudo-code.
It's a clean, simple model of history.

```py
# a file is a bunch of bytes
blob: list[bytes] = ...

# a directory contains named files and directories
tree: dict[str, blob | tree] = ...

# a commit has parents, metadata, and the top-level tree
commit = {
    parents: list[commit]
    author: str
    message: str
    snapshot: tree
}
```

An _object_ is a blob, tree, or commit. In Git data store, all objects are content-addressed
by their [SHA-1 hash](https://en.wikipedia.org/wiki/SHA-1). It is important to understand
that commits don't contain objects, rather just have a reference to them using their hash.

## CLI

Using the command-line interface (CLI), commits can be managed. As mentioned, commits are 
immutable. To edit a commit, an old commit has to be removed and a new one created.

### Creating commits

The following command is used to create a commit with a specific commit message:

- `git commit -m "<message>"`

Note that we first need to introduce the concept of _staging_ before creating
commits properly. If you don't want to use staging and directly include all
changes into you commit, you can use the `-a` flag.

It is important to write **good** commit messages. You will thank yourself later.
Here is a [guide](https://cbea.ms/git-commit/) on writing good messages.

### Removing Commits

Multiple commands exist around the notion of removing or reverting changes in a commit.

- `git reset <commit-hash> -- <path>` \
    Resets a file to another commit hash.
- `git revert <commit-hash>` \
    Undoes all changes that have been introduced from the given commit. Note that this 
    command adds a new commit reverting the changes, instead of removing them.
- `git commit --amend` \
    Edits the last commit's contents and message.
