# Linux Setup

This file is meant to summarize a few configs / setups / things to install on my linux environment to be able to work confortably.

## Keyboard remapping

### Problem

Remap keyboard to exchange 5 -> T, F4 -> 5, T -> F4 to work around my broken keyboard.

### Solution

I edited (after backup) the /usr/share/X11/xkb/symbols/fr file, to add at the end a "French Custom" layout.  
I then added an entry in /usr/share/X11/xkb/rules/evdev.lst and evdev.xml in the variant section, to point to this layout. This is necessary to be able to change the keyboard layout from gnome settings : Settings > Region & Language > + > French > Custom.

A probably better solution would have been to create a new file, but I couldn't make that work.

### Note 

I also tried xmodmap, but it seems to be deprecated, but it had a nice UI to edit the layout.

### References

https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions  
https://askubuntu.com/questions/482678/how-to-add-a-new-keyboard-layout-custom-keyboard-layout-definition < this one is nice.


## Custom swipe gestures

`libinput-gestures` lets you define any custom command on 3 or 4 fingers swipes.

Works well but for switching workspaces, it feels laggy because it doesn't stick to fingers. Gnome should however support that by I never managed to make it work so far.

https://github.com/bulletmark/libinput-gestures  
https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/516

## Phone and laptop commmunication

Goal: have an equivalent of AirDrop, to send / receive files, share browser tabs and clipboard.

### Solution

Installing firefox on both devices, logged in with the same account, lets you share tabs easily.

For the rest, KDE developped `KDE Connect` which does exactly that. It was ported to Gnome with [Gnome Connect](https://extensions.gnome.org/extension/1319/gsconnect/).

The clipboard sync doesn't seem to work very reliably, and sometimes the connection is lost for some reason, but overall it's really cool.

## Google Photo backup

I use [gphotos-sync](https://github.com/gilesknap/gphotos-sync) to backup my photos _directly_ to my external hard drive.

The only annoying bit is that it didn't find exactly how I could install it properly, so currently I made a `gphotos-sync` folder under ~/.local/bin, and a Pipenv environment in it with gphotos-sync installed.

So to backup run
```bash
cd ~/.local/bin/gphotos-sync
pipenv run gphotos-sync /media/gregnix/GregWD/Google\ Photo/
```

