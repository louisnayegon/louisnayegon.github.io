## Ruby

### Uninstall All Ruby Gems

```bash
for i in `gem list --no-versions`; do gem uninstall -aIx $i; done
```
