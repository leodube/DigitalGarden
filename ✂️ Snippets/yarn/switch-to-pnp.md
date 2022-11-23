# Switch to Plug'n'Play
1.  Look into your `.yarnrc.yml` file for the [`nodeLinker`](https://yarnpkg.com/configuration/yarnrc#nodeLinker) setting
2.  If you don't find it, or if it's set to `pnp`, then it's all good: you're already using Plug'n'Play!
3.  Otherwise, remove it from your configuration file
4.  Run `yarn install`
5.  Various files may have appeared; check [this article](https://yarnpkg.com/getting-started/qa#which-files-should-be-gitignored) to see what to put in your gitignore
6.  Commit the changes