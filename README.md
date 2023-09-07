# asdf-pony

Pony plugin for the [asdf](https://github.com/asdf-vm/asdf) version manager.

I wrote this for [rtx](https://github.com/jdxcode/rtx) and only tested it with rtx, but it should work just fine with asdf too.

## Install

```
asdf plugin-add pony https://github.com/jgaines/asdf-pony.git
```

or for those using rtx:

```
rtx p i pony https://github.com/jgaines/asdf-pony.git
```

## Changes from Upstream

Links of script names are links into the asdf plugin creation docs.

* Small change to [list-all](https://asdf-vm.com/plugins/create.html#bin-list-all) to filter out ^{} versions.
* Total rewrite of [install](https://asdf-vm.com/plugins/create.html#bin-install) to use ponyup.
* TODO: add [pre-plugin-remove](https://asdf-vm.com/plugins/create.html#bin-pre-plugin-remove) to ask about removing default ponyup
* TODO: add [uninstall](https://asdf-vm.com/plugins/create.html#bin-uninstall) command

## Current State

I'm still working on this as you can see from the TODO's above.  So far, I've been able to successfully install using version numbers returned from `rtx ls-remote pony`, and `rtx i pony@latest`.  I'm not sure I'll ever be able to support git revision installs using ponyup as the install tool, also not sure about daily installs.

## About Using Ponyup

I tried real hard to not use the default install location for ponyup.  But ponyup is too smart for me and kept insisting on doing things at the default install location even though I was passing `--prefix`` to it at every command.  This might be because I already had an existing default install of ponyup so it was thinking it knew better than me.  

Since I couldn't make it stop using the default install, I just decided to roll with it and use the default install.  The upshot of this is that if you already have a default install and use ponyup directly, outside of rtx (or asdf) be aware that this plugin is using it too.

Also if you remove this plugin from your version manager, it will ask if you want to also remove the default install of ponyup.  Just say no if you want to keep it around.
