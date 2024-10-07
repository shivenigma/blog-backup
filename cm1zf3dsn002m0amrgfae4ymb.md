---
title: "My tmux configuration"
datePublished: Mon Oct 07 2024 19:41:00 GMT+0000 (Coordinated Universal Time)
cuid: cm1zf3dsn002m0amrgfae4ymb
slug: my-tmux-configuration
tags: tools, tmux, uses

---

I’ve been using tmux from a very long time from my Ubuntu days. Today I just read [Neil’s notes](https://neilzone.co.uk/2024/10/tmux-my-notes-so-far/) about his tmux experiment, I wanted to share this file with him and chat about tmux and his current terminal experimentations. But looks like he wants to be a hard man to find, there is no contact info available on his website. So I thought why not just post my config file on the internet.

If you haven’t heard about tmux, it is a terminal program that allows complex terminal usage patterns. You can run multiple panes, windows, programs within one actual terminal window in your OS. Their [home page](https://github.com/tmux/tmux/wiki/Getting-Started) might be able to put it in better words than me.

I actually stared using it for working inside ssh instances on flaky internet. It is practically a non-existent problem for me today, we’re all doing cloud. But there were times when I used to ssh into the server directly and edit files there or set things up manually. If your connection dropped, you have to start again. Tmux will let you to reattach yourself again to resume whatever you were doing.

Today I’m using it more of a multi pane, window terminal and not much for the SSH thing. It is a great tool if you started using it and setup a correct configuration for yourself. I attached my current config below, it usually resides at `~/.tmux.conf`.

<iframe style="width:100%;height:1192px" src="https://emgithub.com/iframe.html?target=https%3A%2F%2Fgithub.com%2Fshivenigma%2Fdotfiles%2Fblob%2Fmaster%2F.tmux.conf&amp;style=default&amp;type=code&amp;showBorder=on&amp;showLineNumbers=on&amp;showFileMeta=on&amp;showFullPath=on&amp;showCopy=on"></iframe>

I like the setup for switching the panes with vim style key bindings and the pane splitting with the keys which makes it easier to reason about the split. Another great feature is you can just use `prefix+z` to just make one pane take fullscreen temporarily if you want to focus on that alone while rest of the panes keep running in the background.

This is simple config but gives me a lot of mileage and this stayed mostly unchanged after initial setup. Give it a try yourself and see if tmux helps your mode of working as well.