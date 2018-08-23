## Surround a word with a character

Example of surrounding a word with backticks:

```
cw`ctl+r"`
```

* `cw` - Delete the word the cursor is on, and end up in insert mode.
* ``` - add the first quote.
* `ctrl+r"` - Insert the contents of the `"` register, aka the last yank/delete.
* ``` - add the closing quote.

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
