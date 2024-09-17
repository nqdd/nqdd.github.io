---
title: "Fix Nx missing dependencies"
description: ""
pubDate: 2024-09-17
---
If you use [nx](https://nx.dev/) in Mac, Window and Linux at the same time, you will encounter one of these problems:
- Cannot find module `@nx/nx-darwin-x64`
- Cannot find module `@nx/nx-darwin-arm64`
- Cannot find module `@nx/nx-linux-x64-gnu`
- Cannot find module `@nx/nx-win32-x64-msvc`

To fix this problem, you need to make these dependencies is optional

```json
// package.json
"dependencies": {
  //..
}
"devDependencies": {
  //..
},
"optionalDependencies": {
  "@nx/nx-darwin-arm64": "<your-version>",
  "@nx/nx-darwin-x64": "<your-version>",
  "@nx/nx-linux-x64-gnu": "<your-version>",
  "@nx/nx-win32-x64-msvc": "<your-version>"
}
```

```sh
rm -rf node_modules
# remove your lock file (package-lock.json or yarn.lock,...)
rm yarn.lock
# reinstall dependencies
npm install --include=optional
# or (recommend)
yarn
```
