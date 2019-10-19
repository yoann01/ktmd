---
layout: post
title: npm Memo 
tags: [npm, js]
categories:
- blog
---



## NODEjs

**Update Nodejs**
 Find out which version of Node.js you are using:
```sh
 node --version
```
 Find out which versions of Node.js you may have installed and which one of those you're currently using:
```sh
 nvm ls
```
 List all versions of Node.js available for installation:
```sh
 nvm ls-remote
```
 Apparently for Windows the command would be rather like this:
```sh 
nvm ls available
```
 Assuming you would pick Node.js v8.1.0 for installation you'd type the following to install that version:
```sh
nvm install 8.1.0
```
 You are then free to choose between installed versions of Node.js. So if you would need to use an older version like v4.2.0 you would   set it as the active version like this:
```sh 
nvm use 4.2
```
[update Node.js just using nvm ](https://davidwalsh.name/nvm)

---

## Npm

**Listing globally installed NPM packages and version**

Basic command
```sh
npm -v
npm init # create package.json & add -y is yes to all requirements
npm install # install all packages in package.json
npm install <package> # install in package but not written in package.json
npm install <package> --save-dev # install in modules only in develop dependencies
npm install <package>  --save # install in modules in dependencies
npm install <package>@<version> # install specific version of package
npm cache clean # clear npm cache
npm ls -g # list all modules installed globally
npm ls #  list all modules locally
npm list --depth 0 # list all npm modules with depth 0
npm show <package> # show versions, maintainers
npm outdated # show all outdated modules
npm prune #removes "extraneous" packages. Extraneous packages are packages that are not listed on the parent package's dependencies list.

```

**Range Syntax**

>- caret (^)
Allows changes that do not modify the left-most non-zero digit in the [major, minor, patch] tuple. In other words, this allows patch and minor updates for versions 1.0.0 and above, patch updates for versions 0.X >=0.1.0, and no updates for versions 0.0.X.

“express”: “^4.15.3” means it can upgrade to version 4.99.0. Basically anything before 5.0.0

**Update a package**

>- First find out your outdated packages by typing npm outdated

>- Then update the package or packages that you want manually as npm update –save package_name


```sh
npm list -g --depth=0
```
```sh
C:\Users\paul.redman\AppData\Roaming\npm
├── bower@1.2.5
├── generator-angular@0.4.0
├── generator-karma@0.5.0
├── grunt-cli@0.1.9
├── jake@0.5.18
├── jshint@0.9.1
├── karma@0.8.7
├── nodeunit@0.7.4
└── yo@1.0.4
```

**npm uninstall**
```sh
npm uninstall [<@scope>/]<pkg>[@<version>]... [-S|--save|-D|--save-dev|-O|--save-optional|--no-save]

aliases: remove, rm, r, un, unlink
```

```sh
npm uninstall sax
```

In global mode (ie, with -g or --global appended to the command), it uninstalls the current package context as a global package.

npm uninstall takes 3 exclusive, optional flags which save or update the package version in your main package.json:

>- -S, --save: Package will be removed from your dependencies.

>- -D, --save-dev: Package will be removed from your devDependencies.

>- -O, --save-optional: Package will be removed from your optionalDependencies.

>- --no-save: Package will not be removed from your package.json file.

Further, if you have an npm-shrinkwrap.json then it will be updated as well.

Scope is optional and follows the usual rules for npm-scope.

Examples:

```sh
npm uninstall sax --save
npm uninstall @myorg/privatepackage --save
npm uninstall node-tap --save-dev
npm uninstall dtrace-provider --save-optional
npm uninstall lodash --no-save
```

**NPM update pckgs**
```sh
npm i -g npm-check-updates
npm-check-updates -u
npm install
```
---

## Nvm ( node version manager )

**install**

  _Git install_
  If you have `git` installed (requires git v1.7+):

  1. clone this repo in the root of your user profile
    - `cd ~/` from anywhere then `git clone https://github.com/creationix/nvm.git .nvm`
  1. check out the latest version with `git checkout v0.33.5`
  1. activate nvm by sourcing it from your shell

  Now add these lines to your `~/.bashrc`, `~/.profile`, or `~/.zshrc` file to have it automatically sourced upon login:
  (you may have to add to more than one of the above files)

  ```sh
  export NVM_DIR="$HOME/.nvm"
  [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
  [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
  ```
  nvm-windows

  [NVM-windows](https://github.com/coreybutler/nvm-windows)

**Usage**

NVM for Windows is a command line tool. Simply type `nvm` in the console for help. The basic commands are:

  - `nvm arch [32|64]`: Show if node is running in 32 or 64 bit mode. Specify 32 or 64 to override the default architecture.
  - `nvm install <version> [arch]`: The version can be a node.js version or "latest" for the latest stable version. Optionally specify whether to install the 32 or 64 bit version (defaults to system arch). Set `[arch]` to "all" to install 32 AND 64 bit versions.
  - `nvm list [available]`: List the node.js installations. Type `available` at the end to show a list of versions available for download.
  - `nvm on`: Enable node.js version management.
  - `nvm off`: Disable node.js version management (does not uninstall anything).
  - `nvm proxy [url]`: Set a proxy to use for downloads. Leave `[url]` blank to see the current proxy. Set `[url]` to "none" to remove the proxy.
  - `nvm uninstall <version>`: Uninstall a specific version.
  - `nvm use <version> [arch]`: Switch to use the specified version. Optionally specify 32/64bit architecture. `nvm use <arch>` will continue using the selected version, but switch to 32/64 bit mode based on the value supplied to `<arch>`. For information about using `use` in a specific directory (or using `.nvmrc`), please refer to [issue #16](https://github.com/coreybutler/nvm-windows/issues/16).
  - `nvm root <path>`: Set the directory where nvm should store different versions of node.js. If `<path>` is not set, the current root will be displayed.
  - `nvm version`: Displays the current running version of NVM for Windows.
  - `nvm node_mirror <node_mirror_url>`: Set the node mirror.People in China can use *https://npm.taobao.org/mirrors/node/*
  - `nvm npm_mirror <npm_mirror_url>`: Set the npm mirror.People in China can use *https://npm.taobao.org/mirrors/npm/*



