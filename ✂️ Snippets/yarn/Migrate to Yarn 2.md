# Migrate to Yarn 2
See: https://yarnpkg.com/getting-started/migration

1.  Run `npm install -g yarn` to update the global yarn version to latest v1
2.  Go into your project directory
3.  Run `yarn set version berry` to enable v2 
4.  If you used `.npmrc` or `.yarnrc`, you'll need to turn them into the [new format](https://yarnpkg.com/configuration/yarnrc)
5.  Add [`nodeLinker: node-modules`](https://yarnpkg.com/configuration/yarnrc#nodeLinker) in your `.yarnrc.yml` file
6.  Run `yarn install` to migrate the lockfile
7.  Take a look at [this article](https://yarnpkg.com/getting-started/qa#which-files-should-be-gitignored) to see what should be gitignored
8. Commit the changes