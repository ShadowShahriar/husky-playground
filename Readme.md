<!-- @format -->

# husky-playground

## Prerequisites

```
OS
Windows 10 Pro 20H2
build 19042.1237

node -v
v14.15.5

husky
^7.0.2
```

## Experience

Well, it was easier than I thought 😅

Initially, Husky didn't run after installation. Then I found [this discussion](https://github.com/typicode/husky/issues/445) where [@simo54](https://github.com/simo54) mentioned that [the following](https://github.com/typicode/husky/issues/445#issuecomment-821869101) was working for him:

```
npm install husky --save-dev
npx husky install
npx husky add .husky/pre-commit "npm run test"
git commit -m "custom message"
```

However, it didn't work for me 😅 So I replaced `"npm run test"` to `cmd`, and `.husky/pre-commit` file was created without errors. Woof! 🐶

I needed the command to run on `push` so I renamed `.husky/pre-commit` to `.husky/pre-push` and it worked like a charm! 😄

I replaced `cmd` command to a useful one (for example: `npm run whoa`).

Also, I didn't have to delete `.git/hooks`. Husky fixed the `.git/config` for me:

```
[core]
	...
	hooksPath = .husky
[remote "origin"]
	...
[branch "woof"]
	...
```
