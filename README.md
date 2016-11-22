Intro to Git
============

This file is in a repo which is being used as a hands-on example in the Hackers
at Cambridge Git Workshop 2016. You can find the slides of the presentation [here](https://codepen.io/Moosichu/pen/XNpOeg).

Please give feedback on the workshop at:
[https://goo.gl/forms/wl5QwTJoFYIXDpgc2](https://goo.gl/forms/wl5QwTJoFYIXDpgc2) (not yet live!)

Please follow the setup below before the workshop takes place!

Setup
-----
First thing you will need to do, is install Git! If you already have it installed
skip to the next section, if not, refer to the relevant platforms below:

### Git Installation

#### Windows 10

Go here: https://git-scm.com/download/win

Follow the instructions, leave everything on its default setting.

#### OSx

Go here: https://git-scm.com/download/mac

#### Linux

Go here: https://git-scm.com/download/linux

### Setting the default text editor for git

If you are on Windows, for simplicity, open bash-for-windows and type:
```
git config --global core.editor notepad
```
This is also demonstrated in the [video tutorial](https://youtu.be/fUgs2hOpmFI)

If you are other platforms, the choices available are a lot more flexible.

To change the default text-editor for git commit messages just do the following:
```
git config --global core.editor "editor_name"
```

eg.
```
git config --global core.editor "gedit"
```

Some need custom commands, which you will find on an editor's respective
website. Here are some common examples:

Atom:
```
git config --global core.editor "atom --wait"
```

Sublime:
```
git config --global core.editor "subl -n -w"
```

Although you need to install
[subl](http://www.sublimetext.com/docs/3/osx_command_line.html) for that to
work.


### Setting up the project for the workshop

Follow along with [this](https://youtu.be/fUgs2hOpmFI) video to setup everything you need
for the workshop, the steps are also listed below.

1. Create an account on Github.
2. Fork this repository.
3. Clone this repository.
4. Create a file with a unique name that you think no one else will use!
   (eg. richard_hac.txt)
5. Write a beautiful
   [haiku](https://www.poets.org/poetsorg/text/haiku-poetic-form) in this
   text-file.
6. Open the folder you are in in bash-for-windows/terminal and type
   ``` git add file_name.txt ```, where ``` file_name.txt ``` is the name of the
   file containing your Haiku!
7. Now write ```git commit```, in the text editor, simply add the line:
   "Add YourName's Haiku". Where, YourName is, your name.
8. Finally write ``` git push ``` in the terminal, and you are done!

Notes
=====

Below are some notes from what is being covered in the workshop. You can have a
look at these after the workshop is done. :)

How to write a Git Commit message
---------------------------------
There is no standard way to write a Git commit message! If you look at various
repositories around the web, (eg. [the Linux
Kernel](https://github.com/torvalds/linux/commits/master), [Dolphin Emulator
](https://github.com/dolphin-emu/dolphin/commits/master)), you will find not all
commit messages are consistent.

However, you will notice a trend, and that is as follows:

```
Write imperative title that is less than 50 chars

The body of the message can be as long as you want it to be :) (but
each line should be less than 72 characters). You can write in any
format as long as you give a description of what your changes do and,
most importantly, why the changes were made.

If you need a list, that is easy:
 - You can list something like this
 - Like this

Some repositories will require commits to be signed off, which can go
at the bottom. You will see this a lot in Linux Kernel commits. In fact,
the links above have good examples of commit messages! Although not
every single message follows this format, you will find most of them do.
```

Git Log
-------

Provided Git messages have been written to a consistent format, the Git log is
an incredibly useful tool. Here are a few useful examples of git log with
example outputs:

1)```git log -2```:

```
commit dec1c8344fdfd20f1247bfb9cc9b8035287b767a
Author: Example Author <email@example.com>
Date:   Sun Feb 21 17:56:23 2016 +0000

    Overload SaveReader to allow loading from streams

    All the SaveReader methods now have alternative versions where you can
    pass an InputStream and they will read a save from that.

commit 2ed25caf975beb8b8657912d72081afa98fda799
Author: Example Author <email@example.com>
Date:   Mon Feb 8 13:37:22 2016 +0000

    Fix typo in README.md.
```
2)```git log --pretty=format:"%h %s"```:

```
929757e Make example be correct
870d7ee Add conversion tool for .txt preview to .html preview and its output
3874baa Merge branch 'master' of https://github.com/EchoCam/DynamicNarrative.git
a72cac5 Rename file
7ed0fed Change default logging level to none
28fe093 Fix Scooby Doo text task
4ce23c4 Change names
1b3fb15 Add final story
```

3)```git log --pretty=format:"%h %s" --graph```:

```
* 929757e Make example be correct
* 870d7ee Add conversion tool for .txt preview to .html preview and its output
*   3874baa Merge branch 'master' of https://github.com/EchoCam/DynamicNarrative.git
|\  
| * 7ed0fed Change default logging level to none
* | a72cac5 Rename file
|/  
* 28fe093 Fix Scooby Doo text task
* 4ce23c4 Change names
* 1b3fb15 Add final story

```


Find out more on the official [Git
website](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History).


Rebasing vs Merging
-------------------

Rebasing:

  Git rebasing is a clever way of updating one branch with another branch's new
  commits. The way it works is by finding the common history of the current
  branch and the one being rebased-in. Undoing the current branches commits
  until then and then applying them on top of the branch being rebased-in.

  However, as it changes commit-history, it should only be used on branches
  that no one else can see.

Merging:

  Merging is safer then rebasing but can make slightly more nasty commit
  histories.

A good place to learn more is
[http://pcottle.github.io/learnGitBranching/](http://pcottle.github.io/learnGitBranching/)

Git Blame
---------

Git blame is a powerful tool to work-out who changed a piece of code and who is
responsible for certain aspects to it. You can find out more abuot git blame
[here](https://git-scm.com/docs/git-blame).

The most easy way to use it is:

```
git blame -L<start>,<end> path/to/file
```

eg.

```
git blame -L134,150 README.md
```

To show lines 134 to 150 in README.md

You can find out more about GIt blame
[here](https://git-scm.com/docs/git-blame).

Git Reset vs Git Revert
-------------------------

Finally, Git reset vs Git revert.

### git reset

Git reset has two different scopes depending on the parameters passed,
commit-level and file-level. We will only cover the former, which is when you
pass a specific commit as an argument to the command.

At a commit level, git reset will move the tip of a branch to a different commit,
so is very dangerous! It is an easy way to 'undo' commits that you *haven't yet
made public* and *definetely do not want the history of in any way*.

Another use of git reset, is using 'strength' flags. Such as:
 - ```--soft```, this won't affect the staged snapshot or current working
   directory
 - ```--hard```, this will replace both the staged snapshot and current working
   directory.

So just doing ```git reset --hard``` without anything else is a useful way of
saying "I'm unhappy with my uncommitted changes, let's start afresh."

#### git revert

Git revert is like a safe reset. You simply pass it a specific commit and it
will add a new commit such that it has the same file-contents
as that commit, but appends it to the end of the current branch rather then
rolling everything back, preserving history.

A useful explanation can be found
[here](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting/commit-level-operations).
It also covers Git revert and other aspects not mentioned here!


Special thanks
--------------
 - Christian Silver for his awesome presentation software.
 - All the websites I linked to!
