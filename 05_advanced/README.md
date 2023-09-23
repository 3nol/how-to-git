# Advanced

Here are some more advanced commands, tips and tricks.

## More Commands

- `git config -e [--global]` \
    Lets you edit Git's configuration. The entire configuration is stored
    in a file named `.gitconfig` (see below). Specifying the flag `--global`
    lets you edit the system-wide Git configuration.
- `git add -p <path>` \
    Interactive staging for files. Very useful when only partially adding
    changes of a file.
- `git rebase -i <reference>` \
    Interactive branch operations. This is a very powerful tool which can not
    only rebase, but also reorder, edit, squash, delete, and merge commits.
- `git blame <path>` \
    Shows you who last edited which line in a given file path.
- `git stash [push | pop] -- <path>` \
    Temporarily removes modifications (staged or unstaged) from your working
    directory. Pushing allows you to remove the changes, using `pop` allows
    you to bring back the most recently removed changes. Useful for cleaning
    up you workspace.
- `git cherry-pick <commit-hash>` \
    Copies a given commit from _anywhere_ to the current branch.
- `git cherry <branch-name>` \
    Compares the current branch to a given one. Displays which commits are only
    on one branch and which are on the other.


## Data and config storage

1. `.git/` directory \
    You will find this directory in any Git repository. It is where Git stores
    everything it knows about objects and references. Do not delete it.

2. `.gitconfig` file \
    As mentioned above, Git is [highly customizable](https://git-scm.com/docs/git-config).
    This file stores the entire configuration. You will find a local
    configuration in `.git/config`, while the system-wide Git config is usually
    stored in `~/.gitconfig`.

    An example for a config file can be found in this directory as well. You
    might notice a section of _aliases_ in there. With them, similar to a shell,
    you can define your own commands. The examples you see are ones that I use
    personally. If you want to learn more about aliases, look [here](https://git-scm.com/docs/git-config#Documentation/git-config.txt-alias).

3. `.gitignore` file \
    This special file allows you to [specify](https://git-scm.com/docs/gitignore)
    files which Git should ignore (i.e. never to be tracked). Useful for
    temporary or generated files, like build artifacts.

    You will also find an example for a git-ignore file in this directory.
    This example targets the use in Java development, as all unnecessary files
    that may come up in this environment are ignored there.

## Useful websites

Here are some useful websites to consult when using Git:

- Official documentation: \
    https://git-scm.com/docs
- Git explained for computer scientists: \
    https://eagain.net/articles/git-for-computer-scientists/
- Recovering from common Git mistakes: \
    https://ohshitgit.com
- Generating a `.gitignore` file for a project: \
    https://www.toptal.com/developers/gitignore
- Choosing a license for your public repository, e.g. for GitHub: \
    https://choosealicense.com
