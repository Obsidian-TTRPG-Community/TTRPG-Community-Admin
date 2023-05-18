---
aliases: [Getting Your Feet Wet]
created: 2023-05-17
tags: []
updated: 2023-05-17
---

<--- Back to [Why We Use Git](1-Why-We-Use-Git.md) \| Forward to [Fine Tuning Your Basics](3-Fine-Tuning-Your-Basics.md) --->


The default documentation of [GitHub](https://github.com/git-guides) is very comprehensive and visual, and we recommend you read through them. However, we'll include a Quickstart.

## Setting It Up

- First, create a [Github](https://github.com) account if you haven't already.
- Then, download and install [Git](https://github.com/git-guides/install-git) on your computer.
- Optionally, grab

Once you have Git installed, set it up with your name and email address using the following commands in a terminal or shell window:

```bash
git config --global user.name "Your name here"
git config --global user.email "your_email@example.com"
git config --global color.ui true
```

`git config --global color.ui true` is optional, but it color codes the different messages.

If you already have a preferred editor, like notepad++ or VSCode, also include this next line, otherwise ***skip***:

```bash
git config --global core.editor vscode
```

### SSH or GPG

>This is an optional step for now.

If you are interested in eventually signing your commits, you will need to setup SSH or a GPGkey on your account.

For a guide on setting up SSH, we recommend [Atlassian's SSH Guide](https://www.atlassian.com/git/tutorials/git-ssh).

For a guide on setting up GPG, we recommend [Git-SCM's Guide](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work).

## Using Git

When using git, you'll mostly use a few commands: *add*, *commit*, *push*, *status*, and *diff*. While you can use a Graphic User Interface (GUI) to work with git and GitHub, we recommend learning at some point to use the Command Line Interface (CLI), so I will focus on that.

### Your First Clone

> You have an awesome Character Sheet you want to include on the Obsidian TTRPG Share. You've [Forked](https://github.com/Obsidian-TTRPG-Community/ObsidianTTRPGShare/fork) a copy of the repository. Now What?

You decide you want to install this clone in your documents.

Within your terminal, you may need to navigate to the Documents folder. Using the filesystem on macOS for example, we'll navigate to Documents from Root (`/`).

```bash
# Going to Root
cd /
# Looking at the contents of the directory
ls
# Going to Documents
cd Users/sigrunshepherd/Documents
```

Now, we are in documents. Let's Clone the TTRPG Repo from our fork.

```bash
git clone https://github.com/sigrunixia/ObsidianTTRPGShare.git
# The Folder ObsidianTTRPGShare is now in my Documents. Lets enter it.
cd ObsidianTTRPGShare
```

Assuming your Fork was up-to-date with the main ObsidianTTRPGShare repository, you are now ready to make a branch. 

> A Branch? What is that? Is a Fork not a Branch?

Yes, and no. 

Using the metaphor of trees:
- The primary repository, or source repository, is **TreeA**. 
- A Fork is a duplicate of **TreeA** in every way except that it has your name carved into it. We'll call this TreeA1
- A Branch is Giving **TreeA1** a 100% duplicate clone. We'll call this **TreeA12**.

We'll continue to use this Tree naming convention in this document.

```
# Making a Branch
git checkout -b TreeA12
```

Git should say that checkout is complete. Now, we can make our changes. In your case, you already have the template ready to load in, so in your file manager of choice, you add the template into the `System-Agnostic/Templates` folder.

Now, you need to make **TreeA** look like **TreeA12**. It is time to commit.

### Your First Commit

First you need to add your new template to the "Loading Area."

```
git add System-Agnostic/Templates/my-template.md
```

Then, you need to load to put the template in the vehicle for transport. Commit messages are optional, however, I recommend getting into the habit from the get-go. These messages help others determine what you did in your commit.

```
# Load the Template into Git
git commit -a -m "Template that adds 1d6 Rolls to all Characters"
# -a means All
# -m means Message
# Messages for commits should be wrapped in ""
```

Once submitted, you should get a message like this:

```bash
2 files changed, 107 insertions(+), 1 deletion(-)

create mode 100644 New-to-TTRPG-Community/Github-Newbie/2-Getting-Your-Feet-Wet.md
```

### Your First Push

**TreeA12** is loaded into the vehicle, and now we need to drive them to **TreeA**. This is called a *push*.

```bash
git push origin TreeA12
```

Git will respond with a bunch of messages:

```bash
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 340 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/sigrunixia/TreeA12
 * [new branch]      TreeA12 -> TreeA12
```

Now go back to the Github Website to your ObsidianTTRPGShare Fork, and refresh. After Refresh, you should see a message in yellow up top that indicates that `TreeA12 has had recent pushes` and a button asking to initiate a Pull Request.

### Your First Pull Request

A Pull Request (PR) tells **TreeA** that **TreeA12** has something awesome, and that **TreeA** should adopt it. When you craft your pull request, you send a letter to TreeA. It puts on a pair of glasses, carefully reads it over, and then...

**Option A**: TreeA is a Tree and is Not Sentient, it has no idea what a Pull Request is.
- The Pull Request sits there in perpetuity.
- Sometimes this is due to not creating an issue to the pull request, or following all the terms of a Contributing.MD, which is specific to repo.
- Sometimes, the repository owner filters away all notifications and does not realize a PR came in at all.

**Option B**: TreeA "No Thanks"
- The Repository Owners Closes the pull request without integrating it in.

**Option C**: "This Looks Good, but I need something changed."
- The Repository Owners respond and ask for changes to the PR before they will accept it into TreeA.
	- You make the changes, and then it ends up being one of the other options after the fact.

**Option D**: "This is great!" **TreeA** throws on the character template bling.
- The Repository Owners accept the changes to **TreeA** with no qualms. 

## Next Steps

This was a very, very basic overview of how to clone, commit, push, and send a PR. Next, we'll get into some of the weeds to make sure those procedures are as clean as possible.

<--- Back to [Why We Use Git](1-Why-We-Use-Git.md) \| Forward to [Fine Tuning Your Basics](3-Fine-Tuning-Your-Basics.md) --->