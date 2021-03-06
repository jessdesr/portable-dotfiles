# portable-dotfiles

This is a minimal set of public dotfiles that I _actually use_ (and maintain). Only use what you need. You'll probably find these files the most useful:

- `git` [configuration file and aliases](https://github.com/normful/portable-dotfiles/blob/master/.gitconfig)
- `bash` [aliases](https://github.com/normful/portable-dotfiles/blob/master/.bash_aliases)
- [.vimrc](https://github.com/normful/portable-dotfiles/blob/master/.vimrc) if you're a vimmer

## Git Aliases

This is a listing of the most commonly used git aliases, in roughly the same order that you'd expect to first use them in a project. These assume that you've also added a bash alias for `git` itself with `alias g='git'` in your ~/.bashrc, ~/.zshrc, ~/.profile, or etc.

| command               | action                                                                                        |
|-----------------------|-----------------------------------------------------------------------------------------------|
| `g cl`                | `git clone`                                                                                   |
| `g s`                 | `git status`                                                                                  |
| `g l`                 | `git log` on steroids.                                                                        |
| `g ll`                | Same as the above, but with a summary of the files changed in each commit.                    |
| `g lll`               | Same as the above, except with all changes shown.                                             |
| `g co existing`       | Check out the `existing` branch.                                                              |
| `g cb feature`        | Create and check out a new `feature` branch.                                                  |
| `g sh @`              | Show the `@` commit (a.k.a. the `HEAD` commit).                                               |
| `g a file.txt`        | Stage all changes from a file (potentially dangerous).                                        |
| `g ap file.txt`       | Selectively stage changes from a file (safer).                                                |
| `g unstage file.txt`  | Unstage the staged changes from a file.                                                       |
| `g dc`                | Show the staged changes.                                                                      |
| `g d commit1 commit2` | See the difference between `commit1` and `commit2`.                                           |
| `g cm "message"`      | Commit the staged changes, with a message, without opening an editor.                         |
| `g amendm`            | Amend the current commit's message, without opening an editor.                                |
| `g amend`             | Add the staged changes to the last commit.                                                    |
| `g undo`              | Undo the last commit.                                                                         |
| `g rb`                | Rebase interactively, allowing for squashing, renaming, reordering of commits, etc.           |
| `g fo`                | `git fetch origin`                                                                            |
| `g mergeff`           | Fast-forward merge, if possible.                                                              |
| `g merge`             | Merge, and always write a merge commit, even if it's possible to fast-forward.                |
| `g rh`                | Reset all changes to the `HEAD` commit, but leave untracked files.                            |
| `g cdf`               | Delete all untracked files.                                                                   |
| `g setto commit`      | Set the current branch to a particular `commit`.                                              |
| `g goto commit`       | "Go to" a particular `commit`.                                                                |
| `g rlco`              | Show recent reflog entries involving branch checkouts (i.e. show recent branches you were on) |

Special aliases used for managing local branches are below. They're intended to be used for organizing local branches before pushing publicly to a single public branch that reflects the cumulative effort of the local branches. This allows many local branches to be preserved, yet named consistently and sequentially. This helps workflows that involve frequent rebasing, squashing, refactoring, cherry-picking, amending, resetting, etc.

| command         | action                                                                                     |
|-----------------|--------------------------------------------------------------------------------------------|
| `g cb1 feature` | Create and checkout the first local branch. e.g. `user/local/YYYY-MM-DD/feature-1`         |
| `g cbn`         | Create and checkout the next local branch. e.g. `user/local/YYYY-MM-DD/feature-2`          |
| `g cbpub`       | Create and checkout the public branch if on a local branch. e.g. `user/YYYY-MM-DD/feature` |
| `g cop`         | Checkout the previous local branch. e.g. `user/local/YYYY-MM-DD/feature-1`                 |
| `g con`         | Checkout the next local branch. e.g. `user/local/YYYY-MM-DD/feature-3`                     |
| `g copub`       | Checkout the public branch if on a local branch. e.g. `user/YYYY-MM-DD/feature`            |

The above set of aliases can also be used with branches containing a numeric identifier (i.e. `123` in the examples below). This numeric identifier is intended to be something like a JIRA Issue ID, Pivotal Tracker Story ID, Bugzilla Issue ID, etc.

| command             | action                                                                                         |
|---------------------|------------------------------------------------------------------------------------------------|
| `g cb1 123 feature` | Create and checkout the first local branch. e.g. `user/local/YYYY-MM-DD/123/feature-1`         |
| `g cbn`             | Create and checkout the next local branch. e.g. `user/local/YYYY-MM-DD/123/feature-2`          |
| `g cbpub`           | Create and checkout the public branch if on a local branch. e.g. `user/YYYY-MM-DD/123/feature` |
| `g cop`             | Checkout the previous local branch. e.g. `user/local/YYYY-MM-DD/123/feature-1`                 |
| `g con`             | Checkout the next local branch. e.g. `user/local/YYYY-MM-DD/123/feature-3`                     |
| `g copub`           | Checkout the public branch if on a local branch. e.g. `user/YYYY-MM-DD/123/feature`            |

## Installation

On Debian-based distros:

```
cd ~
git clone https://github.com/normful/portable-dotfiles.git
bash ~/portable-dotfiles/setup.sh
```

## Extras


### Remapping Caps Lock to Escape

1. On Debian-based distros, running `xmodmap remaps_capslock` will result in the following key mappings:

| Key       | Action    |
|-----------|-----------|
| Caps Lock | Esc       |
| Esc       | Nothing   |
| Pause     | Caps Lock |

2. On OS X up to El Capitan:

- Use [Seil](https://pqrs.org/osx/karabiner/seil.html.en) to map Caps Lock to Escape.
- Additionally, KeyRemap4MacBook, a.k.a. [Karabiner](https://pqrs.org/osx/karabiner/) is handy (see the included [config file](https://github.com/normful/portable-dotfiles/blob/master/Library/Application%20Support/KeyRemap4MacBook/private.xml)).

3. On macOS Sierra:

- Seil is no longer necessary for mapping Caps Lock to Escape. macOS does that natively.
- Karabiner no longer works. You must use Karabiner Elements (actively being developed as a necessary rewrite to Karabiner) instead.
    - Note to self: Use settings in these screenshots for now:
        - [Simple Modifications](https://github.com/normful/portable-dotfiles/blob/master/karabiner-elements/Karabiner-Elements-Settings-Simple-Modifications.png)
        - [Function Keys](https://github.com/normful/portable-dotfiles/blob/master/karabiner-elements/Karabiner-Elements-Settings-Function-Keys.png) 
- As an additional fallback, you can use iTerm2's key remapping and its "Send Hex Code" feature conjunction with [Key Codes](https://manytricks.com/keycodes/) to figure out what key codes to send. [These are the settings](https://github.com/normful/portable-dotfiles/blob/master/iTerm/iTerm-Keys-Settings.png) that I use. 

### Windows-style window resizing shortcuts on OS X

Install [BetterTouchTool](https://www.boastr.net/) and import the [config file](https://github.com/normful/portable-dotfiles/blob/master/Library/Application%20Support/BetterTouchTool/bttdata2). It provides the following key bindings:

| Shortcut | Action                                         |
|----------|------------------------------------------------|
| ⌘⇧C      | Resize Window to Bottom Right Quarter / Corner |
| ⌘⇧E      | Resize Window to Top Right Quarter / Corner    |
| ⌘⇧Q      | Resize Window to Top Left Quarter / Corner     |
| ⌘⇧Z      | Resize Window to Bottom Left Quarter / Corner  |
| ⌘⇧W      | Maximize Window to Top Half                    |
| ⌘⇧X      | Maximize Window to Bottom Half                 |
| ⌘⇧A      | Maximize Window Left                           |
| ⌘⇧D      | Maximize Window Right                          |
| ⌘⇧M      | Maximize Window                                |
| ⌘⇧S      | Resize window to Middle Third                  |

You can remember how the above key bindings work by their position on a standard QWERTY keyboard. 

For example, E is at the top right of the 9-key square formed by QWE, ASD, and ZXC, so ⌘⇧E resizes the window to the top right.
