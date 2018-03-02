# SearchReplace.vim

This plugin does one thing well:
 - search for a pattern across multiple files,
 - displays the matches & lets you delete matches you don't want to replace,
 - replace those matches with a new pattern

Based on `ripgrep` and `sed`, so you will need to have those installed.

## Usage

Run `:Search function`. This will open a side window with files matches, as below.

```
### /home/romgrk/github/searchReplace.vim/plugin/searchReplace.vim ###
34: function! s:run(cmd, cwd, Fn)
40:     let opts.on_stdout = function('s:on_stdout')
41:     let opts.on_stderr = function('s:on_stderr')
42:     let opts.on_exit = function('s:on_exit')
46: endfunction
```

From here, press `d` on match lines to remove that match, and press `d` on
filename lines to delete the remove the file from the operation.
When you're satisfied, run `:Replace fu` to have the remaining matches replaced.
Done.


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
