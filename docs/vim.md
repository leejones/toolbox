## Navigation

- `b` to move to the beginning of a word (`B` does the same thing, but works in different cases (e.g. when the cursor is on a non-word character like !)
- `e` to move to the end of a word
- `%` to move between the following opening/closing characters: `( ) [ ] { }` (e.g. when cursor is on the `}` character, pressing `%` will navigate to the coresponding `{` character. 

## Editing

- `s` change the character under the cusor (switchest to insert mode)
- `x` delete characters under and after the cusror in the current line (e.g. `3x` would delete 3 characters)

## Using External Commands

Insert the ouput of an external command:

```
:read !echo "Some text to add"
```

Run highlighted text through an external command and replace the highlighted text with the result of the external command:

```
# highlight the text using Visual mode
!grep ONLY_CERTAIN_LINES
```

The highlighted text will be passed to the command via stdin.

## Search highlighting

Highlight all search results: `:set hlsearch`.

Automatically disable highlighting (by pressing `esc` twice):

```
nnoremap <esc><esc> :silent! nohlsearch<cr>
```

## Operating on search matches using gn

Search for a term: `/termToSearchFor`

Change the next match: `cgn`

Repeat the change for the next match: `.`

See also [Search highlighting (above)](#search-highlighting).

-- http://vimcasts.org/episodes/operating-on-search-matches-using-gn/

## Pasting previous deletes/yanks

List previous deletes/yanks:

```
:reg
```

Paste item 2 for the register after the cursor:

```
"2p
```

Paste item 2 for the register before the cursor:

```
"2P
```

-- https://vim.fandom.com/wiki/Remembering_previous_deletes/yanks

## Folds

* `zf` - create a fold
* `zo` - expand a fold
* `zc` - collapse a fold
* `zd` - delete a fold
* `zO` - expand all folds at cursor
* `zC` - collapse all folds at cursor

### Fold code that's between `{` and `}` braces:

1. Put the cursor on the opening `{`
2. Type `zfa}`

This will create a fold from the opening `{` to its matching `}`. Vim will skip over any nested `{...}` pairs in-between.

-- https://www.linux.com/training-tutorials/vim-tips-folding-fun/


## Surround a word with a character

Example of surrounding a word with with a single quote:

```
cw'ctl+r"'
```

* `cw` - Delete the word the cursor is on, and end up in insert mode.
* `'` - add the first quote.
* `ctl+r"` - Insert the contents of the `"` register, aka the last yank/delete.
* `'` - add the closing quote.

Source: https://stackoverflow.com/questions/2147875/what-vim-commands-can-be-used-to-quote-unquote-words

## Opening multiple files with xargs

To open multiple files without messing up STDIN on your terminal, use `xargs -o` (on OSX/BSD):

```
ls -1 | xargs -o vim
```

Source: https://superuser.com/a/427881

## Recording keystrokes for playback

This is useful for performing the same edit in multiple places.

1. In normal mode, press `q` followed by any letter from `a` to `z` to start a recording named after that letter.
2. Perform the action you want to record.
3. Press `q` from normal mode to end the recording.
4. Replay the recording by pressing `@<letter from earlier>`. Press `@@` replay the last playback. You can also use the `.` key to repeat the last action (playback or otherwise).

Source: http://vim.wikia.com/wiki/Recording_keys_for_repeated_jobs

## Expand tabs

```
:set tabstop=2
:set softabs=2
:set expandtabs
```
