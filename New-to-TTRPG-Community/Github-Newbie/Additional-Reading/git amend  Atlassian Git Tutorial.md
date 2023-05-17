---
aliases: git amend | Atlassian Git Tutorial
author: Atlassian
created: 2023-05-16
source: https://www.atlassian.com/git/tutorials/rewriting-history
tags: []
updated: 2023-05-16
---

## Git Amend | Atlassian Git Tutorial

>[!Excerpts]  
>Common use cases for overwriting committed snapshots in Git. History rewriting commands: git commit--amend, git rebase, git rebase -i and git reflog.

---

### Intro

This tutorial will cover various methods of rewriting and altering Git history. Git uses a few different methods to record changes. We will discuss the strengths and weaknesses of the different methods and give examples of how to work with them. This tutorial discusses some of the most common reasons for overwriting committed snapshots and shows you how to avoid the pitfalls of doing so.

Git's main job is to make sure you never lose a committed change. But it's also designed to give you total control over your development workflow. This includes letting you define exactly what your project history looks like; however, it also creates the potential of losing commits. Git provides its history-rewriting commands under the disclaimer that using them may result in lost content.

Git has several mechanisms for storing history and saving changes. These mechanisms include: Commit `--amend`, `git rebase` and `git reflog`. These options give you powerful work flow customization options. By the end of this tutorial, you'll be familiar with commands that will let you restructure your Git commits, and be able to avoid pitfalls that are commonly encountered when rewriting history.

### Changing the Last Commit: `git Commit --amend`

The `git commit --amend` command is a convenient way to modify the most recent commit. It lets you combine staged changes with the previous commit instead of creating an entirely new commit. It can also be used to simply edit the previous commit message without changing its snapshot. But, amending does not just alter the most recent commit, it replaces it entirely, meaning the amended commit will be a new entity with its own ref. To Git, it will look like a brand new commit, which is visualized with an asterisk (*) in the diagram below. There are a few common scenarios for using `git commit --amend`. We'll cover usage examples in the following sections.

![Git commit amend](https://wac-cdn.atlassian.com/dam/jcr:34fd0826-9e89-4ef1-bce8-b1325cf48306/01-02%20Changing%20the%20Last%20Commit.svg?cdnVersion=1013)

#### Change Most Recent Git Commit Message

Let's say you just committed and you made a mistake in your commit log message. Running this command when there is nothing staged lets you edit the previous commit’s message without altering its snapshot.

Premature commits happen all the time in the course of your everyday development. It’s easy to forget to stage a file or to format your commit message the wrong way. The `--amend` flag is a convenient way to fix these minor mistakes.

```
git commit --amend -m "an updated commit message"
```

Adding the `-m` option allows you to pass in a new message from the command line without being prompted to open an editor.

#### Changing Committed Files

The following example demonstrates a common scenario in Git-based development. Let's say we've edited a few files that we would like to commit in a single snapshot, but then we forget to add one of the files the first time around. Fixing the error is simply a matter of staging the other file and committing with the `--amend` flag:

```
# Edit hello.py and main.py
git add hello.py
git commit 
# Realize you forgot to add the changes from main.py 
git add main.py 
git commit --amend --no-edit
```

The `--no-edit` flag will allow you to make the amendment to your commit without changing its commit message. The resulting commit will replace the incomplete one, and it will look like we committed the changes to `hello.py` and `main.py` in a single snapshot.

#### Don’t Amend Public Commits

Amended commits are actually entirely new commits and the previous commit will no longer be on your current branch. This has the same consequences as resetting a public snapshot. Avoid amending a commit that other developers have based their work on. This is a confusing situation for developers to be in and it’s complicated to recover from.

#### Recap

To review, `git commit --amend` lets you take the most recent commit and add new staged changes to it. You can add or remove changes from the Git staging area to apply with a `--amend` commit. If there are no changes staged, a `--amend` will still prompt you to modify the last commit message log. Be cautious when using `--amend` on commits shared with other team members. Amending a commit that is shared with another user will potentially require confusing and lengthy merge conflict resolutions.

### Changing Older or Multiple Commits

To modify older or multiple commits, you can use `git rebase` to combine a sequence of commits into a new base commit. In standard mode, `git rebase` allows you to literally rewrite history—automatically applying commits in your current working branch to the passed branch head. Since your new commits will be replacing the old, it's important to not use `git rebase` on commits that have been pushed public, or it will appear that your project history disappeared.

In these or similar instances where it's important to preserve a clean project history, adding the `-i` option to `git rebase` allows you to run `rebase interactive`. This gives you the opportunity to alter individual commits in the process, rather than moving all commits. You can learn more about interactive rebasing and additional rebase commands on the [git rebase page](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase).

#### Changing Committed Files

During a rebase, the edit or `e` command will pause the rebase playback on that commit and allow you to make additional changes with `git commit --amend` Git will interrupt the playback and present a message:

```
Stopped at 5d025d1... formatting
You can amend the commit now, with



 git commit --amend



Once you are satisfied with your changes, run



 git rebase --continue


```

#### Multiple Messages

Each regular Git commit will have a log message explaining what happened in the commit. These messages provide valuable insight into the project history. During a rebase, you can run a few commands on commits to modify commit messages.

- Reword or 'r' will stop rebase playback and let you rewrite the individual commit message during.
- Squash or 's' during rebase playback, any commits marked `s` will be paused on and you will be prompted to edit the separate commit messages into a combined message. More on this in the squash commits section below.
- Fixup or 'f' has the same combining effect as squash. Unlike squash, fixup commits will not interrupt rebase playback to open an editor to combine commit messages. The commits marked 'f' will have their messages discarded in-favor of the previous commit's message.

#### Squash Commits for a Clean History

The `s` "squash" command is where we see the true utility of rebase. Squash allows you to specify which commits you want to merge into the previous commits. This is what enables a "clean history." During rebase playback, Git will execute the specified rebase command for each commit. In the case of squash commits, Git will open your configured text editor and prompt to combine the specified commit messages. This entire process can be visualized as follows:

![Git Tutorial: git rebase -i example](https://wac-cdn.atlassian.com/dam/jcr:d01223a6-df25-48b3-87fd-2b9140d9ae2b/03%20Squash%20commits%20for%20a%20clean%20history.svg?cdnVersion=1013)

Note that the commits modified with a rebase command have a different ID than either of the original commits. Commits marked with pick will have a new ID if the previous commits have been rewritten.

Modern Git hosting solutions like Bitbucket now offer "auto squashing" features upon merge. These features will automatically rebase and squash a branch's commits for you when utilizing the hosted solutions UI. For more info see "[Squash commits when merging a Git branch with Bitbucket](https://bitbucket.org/blog/git-squash-commits-merging-bitbucket)."

### Recap

Git rebase gives you the power to modify your history, and interactive rebasing allows you to do so without leaving a “messy” trail. This creates the freedom to make and correct errors and refine your work, while still maintaining a clean, linear project history.

### The Safety Net: Git Reflog

Reference logs, or "reflogs" are a mechanism Git uses to record updates applied to tips of branches and other commit references. Reflog allows you to go back to commits even though they are not referenced by any branch or tag. After rewriting history, the reflog contains information about the old state of branches and allows you to go back to that state if necessary. Every time your branch tip is updated for any reason (by switching branches, pulling in new changes, rewriting history or simply by adding new commits), a new entry will be added to the reflog. In this section we will take a high level look at the `git reflog` command and explore some common uses.

#### Usage

This displays the reflog for the local repository.

```
git reflog --relative-date
```

This shows the reflog with relative date information (e.g. 2 weeks ago).

#### Example

To understand `git reflog`, let's run through an example.

```
0a2e358 HEAD@{0}: reset: moving to HEAD~2
0254ea7 HEAD@{1}: checkout: moving from 2.2 to main
c10f740 HEAD@{2}: checkout: moving from main to 2.2
```

The reflog above shows a checkout from main to the 2.2 branch and back. From there, there's a hard reset to an older commit. The latest activity is represented at the top labeled `HEAD@{0}`.

If it turns out that you accidentally moved back, the reflog will contain the commit main pointed to `(0254ea7)` before you accidentally dropped 2 commits.

`git reset --hard 0254ea7`

Using Git reset, it is now possible to change main back to the commit it was before. This provides a safety net in case the history was accidentally changed.

It's important to note that the reflog only provides a safety net if changes have been committed to your local repository and that it only tracks movements of the repositories branch tip. Additionally reflog entries have an expiration date. The default expiration time for reflog entries is 90 days.

For additional information, see our `git reflog` page. 

### Summary

In this article we discussed several methods of changing git history, and undoing git changes. We took a high level look at the git rebase process. Some Key takeaways are:

- There are many ways to rewrite history with git.
- Use `git commit --amend` to change your latest log message.
- Use `git commit --amend` to make modifications to the most recent commit.
- Use `git rebase` to combine commits and modify history of a branch.
- `git rebase -i` gives much more fine grained control over history modifications than a standard git rebase.

Learn more about the commands we covered at their individual pages:

- [git rebase](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase)
- [git reflog](https://www.atlassian.com/git/tutorials/rewriting-history/git-reflog)
