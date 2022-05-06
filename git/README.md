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
