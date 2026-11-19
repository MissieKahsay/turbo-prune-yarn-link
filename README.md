# turbo prune fails on a Yarn `link:` dependency

```sh
yarn install
npx turbo@canary prune a
```

fails with

```
  x Unable to find any locator for repo-utils@link:./scripts/repo-utils
```

The root `package.json` depends on `"repo-utils": "link:./scripts/repo-utils"`, a plain directory that is not a workspace. Yarn 4 writes it to `yarn.lock` as `repo-utils@link:./scripts/repo-utils::locator=repro%40workspace%3A.`.
