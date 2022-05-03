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

### List pip package versions available

In the following command replace **\<package\>** with the package name

```bash
pip install <package>==
```
