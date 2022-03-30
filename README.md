# Bash Cheat Sheet

This is a cheat sheet for bash shortcuts that help improving productivity. The commands were performed on a Debian 11 machine.

## Shortcuts

### Navigation

| Shortcut     | Description                           |
| ------------ | ------------------------------------- |
| `ctrl` + `a` | Move cursor to beginning of the line. |
| `ctrl` + `e` | Move cursor to end of the line.       |
| `alt` + `f`  | Move cursor forward one word.         |
| `alt` + `b`  | Move cursor back one word.            |
| `ctrl` + `f` | Move cursor forward one character.    |
| `ctrl` + `b` | Move cursor back one character.       |

### Editing

| Shortcut            | Description                                     |
| ------------------- | ----------------------------------------------- |
| `alt` + `d`         | Delete word after the cursor.                   |
| `alt` + `backspace` | Delete word before the cursor.                  |
| `ctrl` + `d`        | Delete character beneath the cursor             |
| `ctrl` + `h`        | Delete character before the cursor              |
| `ctrl` + `k`        | Cut the line after the cursor to the clipboard  |
| `ctrl` + `u`        | Cut the line before the cursor to the clipboard |
| `alt` + `d`         | Cut the word after the cursor to the clipboard  |
| `ctrl` + `w`        | Cut the word before the cursor to the clipboard |
| `ctrl` + `y`        | Paste the last item to be cut                   |

### History

| Shortcut     | Description                       |
| ------------ | --------------------------------- |
| `ctrl` + `r` | Bring up the history search.      |
| `ctrl` + `g` | Exit the history search.          |
| `ctrl` + `r` | Show previous command in history. |
| `ctrl` + `n` | Show next command in history.     |

## Commands

### Git delete multiple branches

```bash
git branch | sed s/^..// | grep -v remainning_branch | xargs -L 1 -t -I {} git branch -D {}
```

If you need to keep more that one branch without being deleted, you can pass a series of items to `grep` portion of code using `grep -v -E "branch|anotherbrach".

For instance, if you had the following branches on a project:

```
$ git branch
* develop
  feature-one
  local
  main
  nwe-local
  test-branch
```

If you want to delete all branches except for `develop` and `main`, the script you'd run is:

```
git branch | sed s/^..// | grep -v -E "main|develop" | xargs -L 1 -t -I {} git branch -D {}
```
