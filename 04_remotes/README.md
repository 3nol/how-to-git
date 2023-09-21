# Remotes

You might ask yourself: how to collaborate with others using these
fancy concepts (branching, merging, ...) while Git only runs on my machine?
The solution is using remote hosts. 

Remotes allow you to sync your work and their versions to a server.
Git has inbuilt support for uploading and downloading the latest updates.

## How to interact with remotes?

You can use Git commands for interacting with remotes. The main way of interaction
is to fetch, merge, modify, and push changes between _branches_. However, this time,
the branches are not living locally on your machine, but are hosted remotely.

### CLI

You can use `git help remote` to read all relevant information on remotes.

- `git remote` \
    List all added remotes. If you have `git clone`'d a repository, then its
    source will be listed here already. 
- `git remote add <remote-name> <url>` \
    Adds a remote under the given name. Commonly, you only have one remote for 
    syncing. It's convention to call this remote `origin`.
- `git fetch` \
    Retrieves all new updates on objects/references from a remote. Does not perform
    any changes locally yet.
- `git pull` \
    Is the same as `git fetch; git merge` where the remote updates are fetched and 
    directly included in your local copy.
- `git branch -u <remote-name>/<branch-name>` \
    Set up the correspondence between local and remote branch. When you pull now,
    changes from the remote branch will directly merged in your current, local branch. 
- `git push` \
    Send the latest changes to remote. For example, if you set up the correspondence,
    then stage changes, and make a commit, pushing will upload this new commit to 
    the remote host.

## Examples for Git remote hosts

- **GitHub**: Git is not [GitHub](https://github.com/). 
    GitHub has a specific way of contributing code to other projects, called _pull 
    requests_. Yes, that name is terrible; it has nothing to do with the `git pull` command.
- **GitLab**: GitHub is not special: there are other hosts, like 
    [GitLab](https://gitlab.com/), which mostly used in research and academia.
    
    [//]: # (Our department hat its own GitLab instance at: https://gitlab.inf.uni-konstanz.de)

- **BitBucket**: Another host, that is mostly used in the corporate world, is 
    [BitBucket](https://bitbucket.org/).
