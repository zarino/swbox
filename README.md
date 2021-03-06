# swbox

A command line interface for **editing files from your box, on your local machine**.

The perfect partner if you're developing ScraperWiki tools, and want to **use your normal text editor** like TextMate or Sublime Text.

Supports two alternative workflows:

1. **Copying** the remote box files to your local machine, then pushing changes.
2. **Mounting** the remote box as a local filesystem, using SSHFS.

## Examples

`swbox clone fegy5tq` – Makes a local copy of fegy5tq@box.scraperwiki.com

`swbox clone g6ut126@free` - Makes a local copy of g6ut126@free.scraperwiki.com

`swbox mount fegy5tq` - Mounts fegy5tq@box.scraperwiki.com as a local filesystem

## How to use

1. Use [npm](https://npmjs.org) to globally install `swbox` ([nvm](https://github.com/creationix/nvm) is really useful and gets your `npm` for free, so if you're new to Node, try that first):

    ```shell
    npm install -g swbox
    ```

    (If you'd prefer not to use npm, you can always `git clone` this repo and run `./prepublish` yourself to get an executable cli.js script which you can add to your `$PATH`)

2. Read the documentation by running `swbox help`

## Requirements

Mounting boxes as local drives requires **Fuse** and **SSHFS**. Both are available on the [Fuse for OS X homepage](http://osxfuse.github.com/).

The `swbox` command line client requires [Node.js](http://nodejs.org).

## Developing swbox

If you are developing `swbox` we recommend that you run the following from the directory
containing your git clone:

```
./prepublish
npm link
```

This will put the command `swbox` in the usual location where npm installs binaries (which
should already be on your PATH), and symlink it so that whenever you change this directory,
those changes are live.

You still need to compile the CoffeeScript to JavaScript before testing a change to swbox,
do that with:

```
./prepublish
```

If you want to use this local in-development version of swbox with a box, then go to the
box's directory and use:

```
npm link swbox
```

Now `swbox = require 'swbox'` will automatically get your local in-development version of swbox.

## Changelog

#### 0.0.11 – pandora's box

* Swbox is now published to npm. `swbox update` is no longer required and has been removed.

#### 0.0.10 – lunch box

* `swbox test` runs .coffee or .js tests in /tool/test directory, using Mocha.

#### 0.0.9 – set-top box

* Rsync reports of "Permanently added [url] to the list of known hosts" no longer fool swbox into thinking the `push`/`clone` operation failed.
* Mentions of "beta.scraperwiki.com" changed to "scraperwiki.com"

#### 0.0.8 – post box

* `swbox push --preview` will show a preview of what would be created/updated/deleted, without changing anything on the remote box.

#### 0.0.7 – heart shaped box

* `<boxName>` can now include an optional `@boxServer` suffix, allowing you to clone and mount boxes on free.scraperwiki.com and ds.scraperwiki.com (eg: via `swbox clone abcd123@free` or `swbox mount wxyz789@ds`)

#### 0.0.6 – junction box

* `swbox sync` renamed to `swbox push` since it doesn't actually sync, it removes any files on the destination that aren't present on the local copy.
* fixed a bug that caused `swbox sync/push` to loop forever when invoked outside of a local box clone
* `swbox clone` no longer takes an optional destination directory – it will always create a clone, in new directory named after the box, in the current working directory
* removed `/swbox` symbolic link in root directory – it's no longer needed
* standardised display of required and optional arguments in help messages

#### 0.0.5 – hotbox

* `swbox sync` command to synchronise local changes inside a clone, back up to the original box

#### 0.0.4 – chocolate box

* `swbox clone` command to clone an entire box's contents to your local filesystem

#### 0.0.3 – cereal box

* added `-oworkaround=rename` to sshfs options, to allow `rsync` and `git` to rename/update files

#### 0.0.2 – cardboard box

* `swbox update` command to download the latest version of swbox

#### 0.0.1 – Initial release

* mounting and unmounting boxes as sshfs drives
* license, help and docs
