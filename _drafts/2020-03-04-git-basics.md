---
layout: post
title: Git basics
subtitle: from CLI
image: /bj-blog/img/20-03-04-git/git-post-img.png
categories: [Linux]
tags: [git, CLI]
# comments: true
lang: en
---
![xkcd]({{ site.baseurl }}/assets/img/20-03-04-git/xkcd.png)

You clone a repository with `git clone URL`. For example, if you want to clone the Git linkable library called SUBDIR, you can do so like this:

	$ git clone URL/SUBDIR

That creates a directory named SUBDIR, initializes a .git directory inside it, pulls down all the data for that repository, and checks out a working copy of the latest version. If you go into the new SUBDIR directory that was just created, you’ll see the project files in there, ready to be worked on or used.

If you want to clone the repository into a directory named something like MYSUBDIR, you can specify the new directory name as an additional argument:

	$ git clone URL/SUBDIR MYSUBDIR

That command does the same thing as the previous one, but the target directory is called MYSUBDIR.[^clone]

Note the source repo is called `origin` and your new local is `master` by default. Later on you can use `git pull origin master`, to get the newest version from remote origin repo.



###

### git status

Example output:

<!--![git status]({{ site.baseurl }}/assets/img/20-03-04-git/git-status.png)-->

To see all the diff in tracked files but are in unstaged state:

    git diff

or

    git diff path/to/a/given/file


### Stage files


`git add -A` stages all changes

`git add .` stages new files and modifications, **without deletions**

`git add -u` stages modifications and deletions, **without new files**

Detail:

`git add -A` is equivalent to `git add .; git add -u`.

The important point about `git add .` is that it looks at the working tree and adds all those paths to the staged changes if they are either changed or are new and not ignored, _it does not stage any 'rm' actions._

`git add -u` looks at all the already tracked files and stages the changes to those files if they are different or if they have been removed. _It does not add any new files, it only stages changes to already tracked files._

`git add -A` is a handy shortcut for doing both of those.[^note2]


If you have already staged the changes with git add, you can see what patch you have staged with[^note1]

    git diff --staged

When you get:

 		! [remote rejected] master -> master (push declined due to email privacy restrictions)

You should issue these command:

		git config --global user.email "XXXX@users.noreply.github.com" # https://github.com/settings/emails
		git rebase -i
		git commit --amend --reset-author
		git rebase --continue
		git push

### More to check alias Todo

 - [git-annex](https://git-annex.branchable.com/)

### Bonus - something totaly different

[Academic Writing in Markdown](https://youtu.be/hpAJMSS8pvs) with special reference to its advantages and features like creating footnotes, bibliographical references.

### Notes

[^note1]: How to see changes to a file before commit? [SO](https://stackoverflow.com/questions/13787109/how-to-see-changes-to-a-file-before-commit/13787903)
[^note2]: Difference between “git add -A” and “git add .” [SO](https://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add)
[^clone]: [(Almost)All about git clone](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)
