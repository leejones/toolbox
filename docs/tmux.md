## Use previous buffers

Bring up a list of recent buffers:

```
ctl + b =
```

Highlighting one and pressing enter will send the contents to the screen.

## Send keyboard input to all panes within a window

```
ctl + b :
set-window-option synchronize-panes on
```

`setw` is the short form of `set-window-option`.

-- based on https://stackoverflow.com/questions/16325449/how-to-send-a-command-to-all-panes-in-tmux

To disable, run the same commands but swap `on` with `off`.

## Copy text to clipboard

Initial setup for iTerm:

* Go to iTerm preferences.
* Under the **General** settings, enable **Applications in terminal may access clipboard**.

Copy text from buffer to clipboard:

* Switch to visual mode: `ctl + b [`
* Navigate the cursor to the beginning of the text you want to copy.
* Enter the highlight mode: `spacebar`
* Navigate the cursor to the end of the text you want to copy
* Copy the text to the clipboard: `enter`
* Paste the text as normal (`cmd + v`) in any other app (including `iTerm`) or paste it using tmux: `ctl + b ]`.

## Resize split panes

`ctl + b esc arrow-key`

## Fullscreen a split pane (zoom)

`ctl + b z`

## Jump to previously used pane

`ctl + b ;`
