---
layout: post
title: Setting up WSL
tags: [wsl, windows, linux, development]
---

It happened once again. A new Windows computer. Starting from scratch. This time due to changing jobs. And being a diligent and thoughtful person, my dotfiles have not been backed up for the past four years. Fortunately, I am a guy who likes his CLI close to default. But every time I reinstall Cygwin or WSL, I am reminded of the small peculiarities I have grown fond of. So as a reminder to my future self, remember these steps the next time you start with clean slates:

## Less cowbell

When double-tapping Tab in order to auto-complete a command or path, you might be exposed to the bell. You may also hear the same sound when attempting (read: failing) to exit vim. Turning it off is a simple matter.

### Turn off the bell for bash

Edit your `~/.inputrc` file, and add the following line:

    set bell-style none

If you want to do this for all users on your system, you can add this to the `/etc/inputrc` file instead.

### Turn off the bell for vim

Same, same, but different. Edit your `~/.vimrc` and add the following lines:

    set visualbell
    set t_vb=

The first line turns off the audio, the second line turns off the visual flashing.

## Let directories be directories

I usually create a symbolic link from my home folder in WSL to wherever my IDE creates new projects, and call this symlink `code`. When I type `cd c` and press the `tab` key, bash autocompletes the line to `cd code`, without the trailing slash. If Ì press `tab` once more, bash adds the trailing slash. The solution is once more to add a line to the fabled `̃/.inputrc` file:

    set mark-symlinked-directories on

## Case insensitive

I don't care if a file or directory is lower-cased or upper-cased when autocompleting. If you are like me, you'd want to add the following to (yes, you guessed it) `~/.inputrc`:

    set completion-ignore-case On

## Closing words

That should be it for now. I dare to claim that 90% of my quarrels with WSL will be fixed by these small changes in configuration. I hope they can be of help to someone else out there.