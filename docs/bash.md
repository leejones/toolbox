## Detect if script input or output is going to a TTY (terminal)

### Format ouput into columns

Create columns based on spaces:

```
$> some-command | column -t
```

Create columns based on tabs:

```
$> some-command | column -t -s $'\t'
```

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

## dig with different DNS server

Use `@x.x.x.x` to specify the DNS server you want to use, for example:

```
dig +short google.com @8.8.8.8
```

## ignore a directory when using find

This example shows all files in PWD except for those in `.git`:

```
find . -not -path "./.git*"
```

## bc command

A basic calculator, for example:

```
echo 1+1+1 | bc
3
```

## paste command

> merge corresponding or subsequent lines of files

Example:

```
echo "20
30
40
50" | paste -s -d+
20+30+40+50
```

BSD version (Mac) doesn't accept input from STDIN so you could do the same with a bash process substitution:

```
paste -s -d+ <(echo "20
30
40
50")
20+30+40+50
```

## store a multi-line string in a variable

```
list=$(cat << EOS
first
second
third
forth
EOS
)
# echo as an array
$> echo $list
first second third forth
# echo with new lines
$> echo "$list"
first
second
third
forth
```

## get help for built-in commands

These commands don't have a man page sometimes (ex. complete, echo, etc)

```
help <command>
help echo
```

## cut text (going backwards)

```
ctl + w
```

## paste text

```
ctl + y
```

## undo typing

```
ctl + -
```

## find where all the inodes are being used

```
find / -xdev -printf '%h\n' | sort | uniq -c | sort -k 1 -n
```

## send a HTTP GET and only display the response headers

```
curl -I -X GET [url]
```

## send the KILL signal (kill -9) to process running in the foreground

```
ctl + \
```

Useful when `ctl + c` doesn't work.

## return the filename of a path

```
basename
```

## return the directory sturture of a path

```
dirname
```
