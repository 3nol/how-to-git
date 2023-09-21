# Branches

Here, we will look at parallel versioning. Imagine, multiple developers want 
to work on a single project but do not want to interfer with each other.
Also, at some point, they want to _merge_ their work again.

Branches model these parallel version timelines for each developer or each
feature you might work on.

## How to split into branches?

Branching allows you to "fork" version history. It can be helpful for working
on independent features or bug fixes in parallel. Branches are completely
independent of each another and only "interact" when merging them again.

You can check which branch you are currently on using:

```
git branch --show-current
```

### CLI

The following command can be used for creating out a branch:

- `git branch [-a]` \
    Lists all existing branches. Specifying `-a` includes all branches,
    even on remote hosts (next chapter).
- `git checkout -b <branch-name>` \
    Creates a new branch and switches to it.
- `git checkout <branch-name>` \
    Switches to an existing branch.

## How to combine branches again?

Merging is the opposite of branching: it allows you to combine forked version
histories, for example, merging a feature branch back into the main branch.

### CLI

To following commands allow you to re-combine existing branches.

- `git merge <branch-name>` \
    Merges a specified branch into the current one. It tries to combine both changes
    using a merging strategy, and prompts you if merge conflicts occur.
- `git rebase <branch-name>` \
    Another way of combining branches. Instead of letting both changes "collide",
    rebasing moves the changes on the current branch _on top_ of the other changes.
    You can remember this by imagining this command setting the other branch as 
    "basis" for your current branch.
- `git branch -d <branch-name>` \
    Deletes a branch. Use only if you are sure that all changes have been merged.

## What are merge conflicts?

When merging branches, conflicts can occur. Git does its best effort in combining
the changes. But in the scenario of changing a certain file in _both_ branches, Git
does not decide for you which change to prioritize.

Instead, you might receive a message like:

```
Auto-merging hello.rb
CONFLICT (content): Merge conflict in HelloWorld.java
Automatic merge failed; fix conflicts and then commit the result.
```

In this case, you have to act. This tutorial does not cover conflict resolution, but
you can read it up on the [official Git documentation](https://git-scm.com/book/en/v2/Git-Tools-Advanced-Merging).