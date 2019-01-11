## Jenkins

### Stop The Service On A Mac

```bash
sudo launchctl unload /Library/LaunchDaemons/org.jenkins-ci.plist
```

### Uninstall On A Mac

```bash
# Run the uninstaller
'/Library/Application Support/Jenkins/Uninstall.command'

# Remove data files
sudo rm -rf /var/root/.jenkins ~/.jenkins
```
