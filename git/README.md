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
