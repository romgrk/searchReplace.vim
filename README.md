# SearchReplace.vim

This plugin does one thing well:
 - search for a pattern across multiple files,
 - displays the matches & lets you delete matches you don't want to replace,
 - replace those matches with a new pattern

**Dependencies**

 - neovim (with floating windows)
 - ripgrep (with `--json` support)
 - sed

WARNING: The supported regex syntax is the intersection of what both `ripgrep`
and `sed` support. Figuring that out is left as an exercice for the reader.

**Neovim only for the moment** (accepting PRs)

[Demo](https://raw.github.com/romgrk/searchReplace.vim/master/static/search-replace.mp4)

## Usage

Run `:Search` to open the prompt window, or `:Search pattern` to search directly.

Add this to your vimrc to open the search prompt quickly.
```vim
nnoremap <silent><C-f> :Search<CR>
```

![:Search](https://raw.github.com/romgrk/searchReplace.vim/master/static/search-replace.png)

From here, press `d` on match lines to remove that match, and press `d` on
filename lines to remove the whole file from the operation.
When you're satisfied, run `:Replace replacement` to have the remaining matches replaced.
Done. (you'll get a `X replacements in Y files` confirmation)

Pattern: a search pattern in a sed/ripgrep compatible format
Directories: a comma separated list of patterns in the gitignore format (`!` makes it an exclude)

See the [docs](./doc/searchReplace.txt) for more keybindings and options.

## Details

The regex patterns supported are the subset of what is supported by both
`ripgrep` and `sed`. Nothing fancy, no look(behind|ahead).

## Configuration

```vim

" Create configuration object if it doesn't exist
let g:searchReplace = get(g:, 'searchReplace', {})

" Closes window on BufLeave event
let g:searchReplace.close_on_exit = v:true

" The edit comment to use to open files
let g:searchReplace.edit_command = 'EditPreviousWindow'

" for example, this can be used to unfocus the search window
" before opening the match
command! -nargs=1 EditPreviousWindow :execute 'wincmd p | edit ' . <f-args>

" Open the search window yourself
let g:searchReplace.open_window = {->execute('aboveleft split')}

```
