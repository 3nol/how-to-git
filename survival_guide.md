# Survival Guide

You are totally new to Git and just want to get going.
Here is what you need to know.

## General Git workflow

When you are working in a directory, you are continuously making changes to files.
Assuming you don't want to use branching and you are working with a remote host, 
the following workflow of commands is what you need:

0. Make changes.
1. `git add <path>` \
    Add the path of the changed files.
2. `git commit -m "<message>"` \
    Include all added files into a commit, attach a _good_ message.
3. `git pull` \
    Download the latest changes (if someone else is working on the repo).
    This makes sure that you always work on the latest state.
4. `git push` \
    Upload your changes to the remote host.
5. Go back to 0.

With `git status`, you can always check the current state of your files.

The following graphic shows the general workflow when using Git.

<div style="text-align: center;">
<img src="https://thepracticaldev.s3.amazonaws.com/i/128hsgntnsu9bww0y8sz.png" width="500px">
</div>

### Common mistakes

Mistakes or inconvenient situations commonly occur when using Git. I can recommend the
website [Oh Shit, Git!?!](https://ohshitgit.com) which covers dealing with Git mistakes.

- **You wrongly added (i.e. staged) files.** \
    Use `git restore --staged <path>` to unstage the files.
- **You made a typo in the last commit message.** \
    Use `git commit --amend` to edit the last message. Make sure you have no staged changes.
- **You did not include a needed change in the last commit.** \
    Stage this change using `git add`, then use `git commit --amend --no-edit` to include
    all staged changes in your last commit.
- **You accidentally created a commit.** \
    If you only want to remove the last commit, but _not_ the changes, use
    `git reset --soft HEAD~1`. If you want to remove the file changes as well,
    use `git reset --hard HEAD~1` instead.
- **You pushed something to a remote which should not be there.**
    - Solution (1) \
        Theoretically, you can remove the commit as should above and force-push the changes.
        You will need force-pushing because you are not going forward in time, but deleting
        a commit from the past. However, that's a) not good practice, and b) force-pushing
        is often disabled on remote branches per default.
    - Solution (2) \
        You can remove the changes you want to exclude, then stage, commit, and push their
        _removal_ as new commit. This is often the better approach. See chapter "01_commits"
        for more information on this.
