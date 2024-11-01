## Add a co-author to a commit message

In the commit message:

```
Normal commit messages stuff...
<new line>
<new line>
Co-authored-by: name <name@example.com>
```

Reference: [GitHub docs](https://help.github.com/en/github/committing-changes-to-your-project/creating-a-commit-with-multiple-authors#creating-co-authored-commits-on-the-command-line)

## Apply a change to another repo as a patch

In the "source" repo, create a patch file from a ref range (just 1 commit in this case):

```
git format-patch --output-directory=/tmp 7305204728076633b760e28d94e46f74556ed160 -1
```

In the "target" repo(s), apply the patch:

```
patch -z "" .docker/Dockerfile /tmp/0001-Use-dl.k8s.io-for-kubectl-install-484.patch
```

`-z ""` tells `patch` not to create a backup.

The first argument is the file to apply the patch to.
