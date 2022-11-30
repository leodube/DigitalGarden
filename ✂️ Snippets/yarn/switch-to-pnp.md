# Switch to Plug'n'Play
1.  Look into your `.yarnrc.yml` file for the [`nodeLinker`](https://yarnpkg.com/configuration/yarnrc#nodeLinker) setting
```yaml
nodeLinker: pnp
```
2.  Run `yarn install`
3.  Various files may have appeared; check [this article](https://yarnpkg.com/getting-started/qa#which-files-should-be-gitignored) to see what to put in your gitignore
4.  Commit the changes