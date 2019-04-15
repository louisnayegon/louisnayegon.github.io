## Python

### Uninstall All Python Packages

#### Mac

```bash
pip freeze | xargs pip uninstall -y
```

#### PC

```cmd
for /f "delims=" %a in ('pip freeze') do (pip uninstall -y %a)
```
