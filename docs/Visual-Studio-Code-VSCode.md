## Collapse/Expand Code

Aka code folding.

### Collapse all code that's within a given object

Click the `>` in the left gutter next to the line number.

### Collapse all code that's within a given object, but show the names of the next level in the hierarchy

Shift + click the `>` in the left gutter next to the line number. For example, if you wanted to collapse `objects` below and only show levels `a`, `b`, and `c` in the following hierarchy:

```jsonnet
objects: {
  a: {
    layers: {
      one: {},
      two: {},
      three: {}
    }
  },
  b: {
    layers: {
      one: {},
      two: {},
      three: {}
    }
  },
  c: {
    layers: {
      one: {},
      two: {},
      three: {}
    }
  }
}
```

The result would be:

```jsonnet
objects: {
  a: { ...
  },
  b: { ...
  },
  c: { ...
  }
}
```

## Open/Close the Terminal

<pre>ctl + `</pre>

## Show Output (e.g `go test` output)

```
cmd + shift + u
```

## Jumping back/forth between definitions and references etc

When ctl clicking on a method to go to its definition or references, VSCode builds a stack of locations visited (like a browser history). Navigate foward/back through the stack with the following keyboard shortcuts:

Go back: `ctl + -` (hyphen)
Go forward: `ctl + _` (underscore)

## Editing Multiple Lines/Locations at Once

To edit multiple lines/locations at once:

1. `option + click` each place in the document you want to edit
1. make the edit(s)
1. press `esc` to end this mode

-- [video from Scott Hanselmman](https://youtu.be/5CmjW_8ief4?t=545)
