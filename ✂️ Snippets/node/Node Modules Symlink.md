# Node Modules Symlink
This is useful for code that is saved to iCloud. Note: Remember to update `.gitignore`

```bash
mv node_modules node_modules.nosync && ln -s node_modules.nosync node_modules
```