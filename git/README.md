## Git

### Clean Submodules

```bash
git clean -xfd
git submodule foreach --recursive git clean -xfd
```

### Reset Submodules

```bash
git reset --hard
git submodule foreach --recursive git reset --hard
```

### Update Submodules Recursively

```bash
git submodule update --init --recursive
```

### Adding a directory as safe

If you get an error
**fatal: unsafe repository (REPO is owned by someone else)**

You can make the repoistory directory safe with the following command.

This example makes **/home/repo** a safe directory globally.

```bash
git config --global --add safe.directory /home/repo
```

### Merge into forked repo

Make sure the origin repo is configured as upstream.
Run the following command to see what remote repos you have

```bash
git remote -v
```

If the original repo is not shown then run the following command where url is the **url** of the original repo

```bash
git remote add upstream <url>
```

If you run the previous command you should now see the upstream repo listed

To merge from the original to the fork perform the following commands

```bash
git fetch upstream
git checkout master
git merge upstream/master
git push
```
