## Detect if script input or output is going to a TTY (terminal)

### Input is a TTY

```
if [[ -t 0 ]]; then
  echo "input is a TTY"
else
  echo "input is another script (e.g. a pipe)"
fi
```

### Output is a TTY

```
if [[ -t 1 ]]; then
  echo "output is a TTY"
else
  echo "output is another script (e.g. a pipe)"
fi
```

--seen on https://stackoverflow.com/questions/911168/how-to-detect-if-my-shell-script-is-running-through-a-pipe

## Helpful shell settings for scripts

```
set -o errexit
set -o errtrace
set -o nounset
set -o pipefail
```

* `errexit` - Exit immediately if a command exits with a non-zero status.
* `errtrace` - If set, the ERR trap is inherited by shell functions.
* `nounset` - Treat unset variables as an error when substituting.
* `pipefail` - the return value of a pipeline is the status of the last command to exit with a non-zero status, or zero if no command exited with a non-zero status

There's more details on why to use these settings in [Safer bash scripts with 'set -euxo pipefail'](https://vaneyckt.io/posts/safer_bash_scripts_with_set_euxo_pipefail/).

## Debug a script

Prints out the commands as they run. Is helpful for finding the line where the scripts errors or slows down etc:

```
bash -x <your script>
```

You can also add `-v` for more verbose output.

## Generate a random password

```
openssl rand -base64 14 | shasum | cut -d ' ' -f 1
```