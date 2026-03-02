---
layout: post
title: "Cheatsheet for ranger FM"
subtitle: Some keybindings
categories: [Linux]
tags: [Ranger FM, CLI, viewmode]
image: /bj-blog/img/20-02-02/ranger-logo.png
lang: en
---
[Ranger fm](https://github.com/ranger/ranger), is a console based file manager (fm) on Unix/Linux. It has a special three-column view features (that is called [Miller columns](/2019-07-17-miller-columns/)), but it is also able to behave as a dual-pane fm, like Midnight Commander (MC), total commander, etc. (Actually many keys work like in MC. It is really a great application with many features that can be customized according to one's need. However, users who are not familiar with terminal commands and vim flavour editors, may find it difficult to learn Ranger's functioning. This is because a lot of keybindings (e.g. `gg`) and terms like "[yank](https://ell.stackexchange.com/questions/14632/why-does-yank-in-vim-mean-copy)" or "[pager](https://unix.stackexchange.com/questions/144016/what-is-a-pager)" have long history in computing.

Some notable features of ranger are:
 - image preview - cf. [demo](https://youtu.be/DJhDMxMgzC0);
 - pdf preview as image;
 - integration with fzf fuzzy searching tool. cf. [instructions](https://github.com/gotbletu/shownotes/blob/master/ranger_file_locate_fzf.md) and [demo](https://youtu.be/C64LKCZFzME);
 - switching between columns-mode (Miller) and multi-pane mode (MC);
 - it is aware of version control systems and displays information.

![ranger in dual-pane mode]({{ site.baseurl }}/assets/img/20-02-02/ranger-mc-mode.png)


When you hit <kbd>?+k</kbd> in ranger, you will get your predefined keybindings set in `~/.config/ranger/rc.conf` file. The only things I changed right after installing ranger, were the <kbd>Delete</kbd> and <kbd>F8</kbd> keys' behavior. I binded to `trash-put` command rather than the default `console delete` (that is rm command in a shell). In this way files that are deleted/removed with del key, can be restored from `~/.local/share/Trash` folder either manually or with `trash-restore` command. I got this idea from this [video](https://www.youtube.com/channel/UCkf4VIqu3Acnfzuk3kRIFwA) by Gotbletu, who is one of the greatest evangelist for ranger and CLI.

### Multi-tabs / multi-panes:

| Keys                    | Action                                                             |
|:------------------------|:-------------------------------------------------------------------|
| <kbd>Ctrl+n</kbd> or gn | create new tab                                                     |
| <kbd>Tab</kbd>          | switch to next tab                                                 |
| <kbd>Ctrl+w</kbd>       | close current tab                                                  |
| <kbd>~</kbd>            | switch `viewmode` by this you can switch to MC-like dual-pane mode |

### File operations:

| Keys               | Action                           |
|:-------------------|:---------------------------------|
| <kbd>c+w</kbd>     | rename file                      |
| <kbd>yy</kbd>:     | copy file                        |
| <kbd>pp</kbd>:     | paste file                     | |
| <kbd>dd</kbd>:     | cut file                         |
| <kbd>Insert</kbd>: | touch, ie. create new file       |
| <kbd>Enter</kbd>:  | open file with default app       |
| <kbd>r</kbd>:      | open file with custom app        |
| Space              | select file(s)                   |


### Folder / Directory

 - F7: or :mkdir create directory
 - dd: cut directory
 - yy: copy directory
 - pp: paste directory

### Navigation

gh go home, change to ~ (home) folder

[Ranger Cheatsheet](https://gist.github.com/heroheman/aba73e47443340c35526755ef79647eb)

## Related applications:
 - [lf - file manager](https://github.com/gokcehan/lf)
 - [nnn](https://github.com/jarun/nnn#features) file manager, available from your distro repo
 - Vifm, standalone app and Vim plugin
