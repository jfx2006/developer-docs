---
description: How to lint and format code.
---

# Lint and Format Code

Thunderbird's source code is linted and formatted using automated tools, which provides several benefits that include:

* ensuring a consistent formatting style across the code base
* preventing formatting issues from taking up developer time in code review
* catching problems that might otherwise go unnoticed
* making it easier for developers to write well-formatted code

Mozlint is a library that standardizes linter configuration and provides an interface for running all linters at once. It's is designed to be consumed by things like mach and taskcluster.

For JavaScript code we use both:

* [eslint](https://eslint.org/) - linting tool
* [Prettier](https://prettier.io/) - formatting tool

These tools can be used via the command line or right in your code editor.

## Configuring mach (optional)

`mach lint`is the command line interface to Mozlint. To use the Thunderbird linter configurations, add the hidden option `--config-path` when running.

```text
$ ./mach lint --config-path=comm/tools/lint path/to/file.js
```

The path given to `--config-path` is relative to the mozilla-central source.

### Add an alias to mach

So you don't have to remember the extra option, you can set up an alias in your `~/.mozbuild/machrc` file.

```text
[alias]
commlint = lint --config-path=comm/tools/lint
```
Now `mach commlint` is the same as running `mach lint --config-path=comm/tools/lint`. See [mach settings](https://firefox-source-docs.mozilla.org/mach/settings.html) for more details.

### Suite code

The mozlint configuration files in `comm/tools/lint` are written so that they can be shared with the Seamonkey project. Thunderbird developers may want to set `MOZLINT_NO_SUITE=1` in their environment so `mach lint` will not check `comm/suite/` or `comm/editor`. Taskcluster will also set `MOZLINT_NO_SUITE` when running lint checks.


## Using the Command Line

After editing some JavaScript code, navigate to the `comm/` directory. \(The following commands need to be run from the `comm/` directory so that Prettier will use the `comm/.prettierignore` file, and not the `.prettierignore` file in the directory just above `comm/`. See [Prettier issue 4081](https://github.com/prettier/prettier/issues/4081).\)

For a single file, run this command, which will attempt to automatically fix any linting or formatting problems:

```text
$ ../mach lint path/to/a/file.js --fix
```

Or for all the files in a given directory:

```text
$ ../mach lint path/to/a/directory/ --fix
```

To simply report any problems but not attempt to automatically fix them, just omit the `--fix` flag:

```text
$ ../mach lint path/to/a/file.js
```

## In a Code Editor

Most popular code editors offer plugins for eslint and Prettier. We highly recommend installing a plugin for eslint and a plugin for Prettier so you can lint and format your code as you are editing it. Issues will be highlighted as you type and you can have Prettier format your code with a few key strokes.

Here are links to plugins for various editors:

* [eslint plugins](https://eslint.org/docs/user-guide/integrations) for various editors
* [Prettier plugins](https://prettier.io/) for various editors

Some of us on the Thunderbird team use the VS Code editor with these plugins:

* [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

  VS Code plugin by Esben Petersen

* [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

  VS Code plugin by Dirk Baeumer

## Via Taskcluster \(In progress\)

Work is progressing on running mozlint-based checks on Taskcluster. For now, the checks are only running on try-comm-central as many of them are failing. As they are "greened-up" they will be added to comm-central.

## Via Mercurial Hooks \(Not Currently Set Up\)

Mercurial has hooks that could be used to automatically check for linting and formatting issues, say when you make a commit.

_Note that we do not currently have this set up for the Thunderbird code base. Initial attempts to use these hooks \(as they are used for Firefox code\) have not succeeded._

**This should be possible now with the recent addition of the --config-path parameter.**

## More Details

* ['Linting' on firefox-source-docs](https://firefox-source-docs.mozilla.org/tools/lint/index.html)
* ['Formatting JS Code With Prettier and eslint' on MDN](https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/Coding_Style/Formatting_JS_Code_With_Prettier_and_eslint)

