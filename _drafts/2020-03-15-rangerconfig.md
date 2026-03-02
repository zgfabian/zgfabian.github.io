---
layout: post
title: Ranger custom configuration
image: /bj-blog/img/20-02-02/ranger-logo.png
categories: [Linux]
tags: [CLI, ranger, configuration]
lang: en
---
Configuration files are located at /etc/range/config/

 - `commands.py`: contains various functions' implementation, written in Python, used to modify ranger's behavior,
 - `rc.conf`: is used for setting various options and binding the keys to functions,
 - `rifle.conf`: decides which program to use for opening which file,
 - `scope.sh`: is a shell script used to generate the previews for various file types.

It's quite common to use `ranger --copy-config=all` to copy the default config files to `~/.config/ranger` and modify them there.

    ranger --copy-config=all
    creating: ~/.config/ranger/rifle.conf
    creating: ~/.config/ranger/commands.py
    creating: ~/.config/ranger/commands_full.py
    creating: ~/.config/ranger/rc.conf
    creating: ~/.config/ranger/scope.sh
