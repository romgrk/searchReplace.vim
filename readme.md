# SearchReplace.vim

This plugin does one thing well:
 - search for a pattern across multiple files,
 - displays the matches & lets you delete matches you don't want to replace,
 - replace those matches with a new pattern

Based on `ripgrep` and `sed`, so you will need to have those installed.

**Neovim only for the moment** (accepting PRs)

## Usage

Run `:Search function`. This will open a side window with files matches, as below.

![:Search](https://raw.github.com/romgrk/searchReplace.vim/master/static/window.png)

From here, press `d` on match lines to remove that match, and press `d` on
filename lines to remove the whole file from the operation.
When you're satisfied, run `:Replace fu` to have the remaining matches replaced.
Done. (you'll get a `X replacements in Y files` confirmation)


## Details

The regex patterns supported are the subset of what is supported by both
`ripgrep` and `sed`. Nothing fancy, no look(behind|ahead).

The arguments of `:Search` are passed as is to `ripgrep`, so you can provide
additionnal options (e.g. glob pattern for files: `Search func *.vim`).


## Configuration

```vim
" Closes window on BufLeave event
let g:searchReplace_closeOnExit = v:true
```
