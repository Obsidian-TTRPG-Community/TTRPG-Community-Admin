---
aliases: Source Code Management  Atlassian Git Tutorial
author: Atlassian
created: 2023-05-16
source: https://www.atlassian.com/git/tutorials/source-code-management
tags: []
updated: 2023-05-16
---

## Source Code Management | Atlassian Git Tutorial

>[!abstract]  
>Source code management (SCM) is used to track modifications to a source code repository. Learn about the benefits and best practices of SCM here.

---

![Rewriting history](https://wac-cdn.atlassian.com/dam/jcr:8e57216e-269e-49e6-aff2-5c03b8512e73/hero.svg?cdnVersion=1013)

Source code management (SCM) is used to track modifications to a source code repository. SCM tracks a running history of changes to a code base and helps resolve conflicts when merging updates from multiple contributors. SCM is also synonymous with Version control. 

As software projects grow in lines of code and contributor head count, the costs of communication overhead and management complexity also grow. SCM is a critical tool to alleviate the organizational strain of growing development costs.

### The Importance of Source Code Management Tools

When multiple developers are working within a shared codebase it is a common occurrence to make edits to a shared piece of code. Separate developers may be working on a seemingly isolated feature, however this feature may use a shared code module. Therefore developer 1 working on Feature 1 could make some edits and find out later that Developer 2 working on Feature 2 has conflicting edits.

Before the adoption of SCM this was a nightmare scenario. Developers would edit text files directly and move them around to remote locations using FTP or other protocols.

- Developer 1 would make edits and Developer 2 would unknowingly save over Developer 1’s work and wipe out the changes.

SCM’s role as a protection mechanism against this specific scenario is known as Version Control

SCM brought version control safeguards to prevent loss of work due to conflict overwriting. These safeguards work by tracking changes from each individual developer and identifying areas of conflict and preventing overwrites. SCM will then communicate these points of conflict back to the developers so that they can safely review and address.

This foundational conflict prevention mechanism has the side effect of providing passive communication for the development team. The team can then monitor and discuss the work in progress that the SCM is monitoring. The SCM tracks an entire history of changes to the code base. This allows developers to examine and review edits that may have introduced bugs or regressions.

### The Benefits of Source Code Management

In addition to version control SCM provides a suite of other helpful features to make collaborative code development a more user friendly experience. Once SCM has started tracking all the changes to a project over time, a detailed historical record of the projects life is created. This historical record can then be used to [‘undo’ changes](https://www.atlassian.com/git/tutorials/undoing-changes) to the codebase. The SCM can instantly revert the codebase back to a previous point in time. This is extremely valuable for preventing regressions on updates and undoing mistakes.

The SCM archive of every change over a project's life time provides valuable record keeping for a project's release version notes. A clean and maintained SCM history log can be used interchangeably as release notes. This offers insight and transparency into the progress of a project that can be shared with end users or non-development teams.

SCM will reduce a team’s communication overhead and increase release velocity. Without SCM development is slower because contributors have to take extra effort to plan a non-overlapping sequence of develop for release. With SCM developers can work independently on separate branches of feature development, eventually merging them together.

SCM is a huge aid to engineering teams that will lower development costs by allowing engineering resources to execute more efficiently. SCM is a must have in the modern age of software development.

### Source Code Management Best Practices

#### Commit Often

Commits are cheap and easy to make. They should be made frequently to capture updates to a code base. Each commit is a snapshot that the codebase can be reverted to if needed. Frequent commits give many opportunities to revert or undo work. A group of commits can be combined into a single commit using a rebase to clarify the development log.

#### Ensure You're Working from Latest Version

SCM enables rapid updates from multiple developers. It’s easy to have a local copy of the codebase fall behind the global copy. Make sure to [git pull](https://www.atlassian.com/git/tutorials/syncing/git-pull) or fetch the latest code before making updates. This will help avoid conflicts at merge time.

#### Make Detailed Notes

Each commit has a corresponding log entry. At the time of commit creation, this log entry is populated with a message. It is important to leave descriptive explanatory commit log messages. These commit log messages should explain the “why” and “what” that encompass the commits content. These log messages become the canonical history of the project’s development and leave a trail for future contributors to review.

#### Review Changes before Committing

SCM’s offer a ‘staging area’. The staging area can be used to collect a group of edits before writing them to a commit. The staging area can be used to manage and review changes before creating the commit snapshot. Utilizing the staging area in this manner provides a buffer area to help refine the contents of the commit.

#### Use Branches

Branching is a powerful SCM mechanism that allows developers to create a separate line of development. Branches should be used frequently as they are quick and inexpensive. Branches enable multiple developers to work in parallel on separate lines of development. These lines of development are generally different product features. When development is complete on a branch it is then merged into the main line of development.

#### Agree on a Workflow

By default SCMs offer very free form methods of contribution. It is important that teams establish shared patterns of collaboration. SCM workflows establish patterns and processes for merging branches. If a team doesn't agree on a shared workflow it can lead to inefficient communication overhead when it comes time to merge branches.

### Summary

SCM is an invaluable tool for modern software development. The best software teams use SCM and your team should too. SCM is very easy to set up on a new project and the return on investment is high. Atlassian offers some of [the best SCM integration tools in the world](https://bitbucket.org/product) that will help you get started.
