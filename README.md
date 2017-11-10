# git-hooks-plus

[![NPM version](https://badge.fury.io/js/git-hooks-plus.svg)](https://www.npmjs.com/package/git-hooks-plus) [![Build Status](https://travis-ci.org/xcatliu/git-hooks-plus.svg)](https://travis-ci.org/xcatliu/git-hooks-plus) [![Coverage Status](https://coveralls.io/repos/xcatliu/git-hooks-plus/badge.svg?branch=git-hooks-plus&service=github)](https://coveralls.io/github/xcatliu/git-hooks-plus?branch=git-hooks-plus) [![Dependency Status](https://david-dm.org/xcatliu/git-hooks-plus.svg)](https://david-dm.org/xcatliu/git-hooks-plus) [![npm](https://img.shields.io/npm/dm/git-hooks-plus.svg?maxAge=2592000)](https://www.npmjs.com/package/git-hooks-plus)

> `git-hooks-plus` is forked from [git-hooks-js](https://github.com/tarmolov/git-hooks-js) and supports Windows.

`git-hooks-plus` is an utility for managing and running project [git hooks](http://git-scm.com/docs/githooks) for [nodejs](http://nodejs.org/) projects.

It has zero dependecies and easy to use.

Just [install git-hooks](#install) and it will run your hooks when a hook is called by git.

## Why do you need git hooks in your project?
Hooks are little scripts you can place in `$GIT_DIR/hooks` directory to trigger action at certain points.

They are very powerful and helpful.

You can do a lot of things with them:

  * [Validate code](http://jshint.com/) and run tests before commit.
  * [Check codestyle](http://jscs.info/).
  * Spell check the commit message or check it format.
  * and etc.

**Note.** When you use `git-hooks-plus`, you should not modify `$GIT_DIR/hooks` directory manually because `git-hooks-plus` will do it for you.

## Supported platforms
  * Unix
  * macOS
  * Windows

## Install
Install `git-hooks-plus` in your project.
```bash
npm install git-hooks-plus --save-dev
```

To keep things organized, `git-hooks-plus` looks for scripts in sub-directories named after the git hook name.
All these sub-directories should be stored in `.githooks` directory in the project root.

Let's create some dummy pre-commit hook.
```bash
mkdir -p .githooks/pre-commit
echo -e '#!/usr/bin/env node' "\nconsole.log('hi!');" > .githooks/pre-commit/hello.js
chmod +x .githooks/pre-commit/hello.js  # This may not working in Windows, but don't worry, hello.js will be executed through node
```

Then just try to commit and see how things are rolling.
```bash
git add .githooks package.json
git commit -m "Add git-hooks"
```

See also [hooks examples](examples).

It's worth to mention that our library checks for gitignore rules while executing scripts in .githooks/ directories.

## Related projects
  * Original [git-hooks](https://github.com/icefox/git-hooks) project
  * [pre-commit](https://github.com/observing/pre-commit)
  * [husky](https://github.com/typicode/husky)
