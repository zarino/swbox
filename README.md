# swbox

A command line interface for interacting with ScraperWiki boxes

## Requirements

Mounting boxes as local drives requires **Fuse** and **SSHFS**. Both are available on the [Fuse for OS X homepage](http://osxfuse.github.com/)

The `swbox` command line client requires [Node.js](http://nodejs.org) and [CoffeeScript](http://coffeescript.org) to be installed.

## How to use

1. Git clone this repo and put it somewhere safe.

2. Run this from inside the repo: `echo "export PATH=\$PATH:$(pwd)" >> ~/.bash_profile; source ~/.bash_profile`

3. Read the documentation by running `swbox help`

## Features (in priority order)

* `swbox mount <boxName>` – mount a box as a drive, using `sshfs`
* `swbox unmount <boxName>` – unmount a box previously mounted using `sshfs`
* `swbox link <localDirectory> <boxName>` – pair a local directory to a box, for later syncing
* `swbox sync` (run from inside a previously `link`ed directory) – rsync directory contents up to box 