# React-Rails-Software-Writing
# Table of contents
1. [Overview](#overview)
    1. [Setup](#setup)
    2. [Tools-Ruby-JS](#conclusion)
2. [Javascript](#js)
    1. [Introduction](#introduction)
    2. [Tools-Ruby-JS](#conclusion)

## Overview
### Setup <a name="setup"></a>

The purpose of these instructions is to give you a basic setup for the React environmnet.

⚠️ **Try to look at these instructions with a critic eye**. The goal is not for you to skim over the content and blindly copy/paste the terminal commands. **Read them** first, and ask yourself, what is it going to do? You may already have 95% of the tools installed on your computer, so no need to re-install them. For every install command, we give you the check command afterwards. Maybe you can run it first to see if the tool is already there? Just a hint 🤓

Let's start!

### Oh-my-zsh

You should already have [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh), a delightful framework for your `zsh` shell. This tool is configured thanks to the `~/.zshrc` file. Go ahead and have a look at it:

```bash
cat ~/.zshrc
```

You can also open this file in Sublime Text to inspect it.

### Node

Node.js is the Framework to run JavaScript outside your browser (server-side, or in your terminal). To install it, run the following commands:

#### OSX

You should already have [Homebrew](https://brew.sh/) installed.

```bash
brew install node
# or: brew upgrade node
```

Check that node is installed with the following commands:

```bash
node -v # should output something bigger than 8.0
type -a node # should be '/usr/local/bin/node'
```

#### Ubuntu

```bash
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
```

Then check that `node -v` yields a version bigger than `8.0`.

### Yarn

[Yarn](https://yarnpkg.com/lang/en/) is the new dependency management tool you can use with NPM packages. It's a replacement over the `npm` command line which comes by default with Node.js.

#### OSX

To install `yarn` on your terminal, knowing you already have Node.js installed, run this:

```bash
brew install yarn
```

Check everything went smoothly with:

```bash
yarn -v # should be greater than 1.0
type -a yarn # should be '/usr/local/bin/yarn'
```

#### Ubuntu

To install `yarn` on Linux, you first need to configure the repository where to download it:

```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

# Then install yarn:
sudo apt-get update && sudo apt-get install yarn
```

Then type `yarn -v` to check it's installed. Version should be greater than `1.0`.

### $PATH

Do you remember what is `$PATH`? [Read this](https://help.ubuntu.com/community/EnvironmentVariables#File-location_related_variables). Basically, it's a list of folders where your operating system look when you type a command. When you type `ls`, the OS will look in the `$PATH` and see that `/bin` is in there. And `/bin/ls` exists! So it will run `/bin/ls`. That means that `ls` is just a **shortcut** for typing the whole path `/bin/ls`. Handy, isnt' it?

Run the following command:

```bash
echo $PATH | tr : \\n
```

You should have something like this:

```bash
./bin
./node_modules/.bin
/Users/<nickname>/.rbenv/shims
/usr/local/bin
/usr/bin
/bin
/usr/sbin
/sbin
```

The two first lines are interesting.

1. `./bin` is useful when you work on a Ruby project using Bundler. [Binstubs](http://bundler.io/v1.10/bundle_binstubs.html) are files that live in the local `bin` folder of your project and can be executed from the command line. We used to prefix all our commands (`rails`, `rake`, etc.) with `bundle exec`. Thanks to binstubs, we can create a little file we can call with `./bin/rails` or `./bin/rake`. Having `./bin` in the `$PATH` means that we can simply type `rails` or `rake` to run this file. Very transparent!
2. `./node_modules/.bin` is something you might not have. Open your `~/.zshrc` file with Sublime Text and update the `export PATH` line. [This is what you should have](https://github.com/lewagon/dotfiles/blob/master/zshrc#L22). Having `./node_modules/.bin` in the `$PATH` means that we'll be able to run executables from the NPM packages we download on a project. That will be useful for ESLint and Webpack. Instead of running `./node_modules/.bin/eslint` we can just type `eslint`! Again, very transparent :)

Once you've updated your `~/.zshrc`, save it, close all your terminals and restart. Run the following again:

```bash
echo $PATH | tr : \\n
```

All good?

### Sublime Text

If you don't have it already, please install the `Babel` package to use the ES6 syntax in Sublime. Don't remember [how to install a package](https://www.google.com/search?q=sublime+how+to+install+a+package)?

## Tools-Ruby-JS <a name="conclusion"></a>

You are now ready to work with a modern JavaScript environment, using ES6 syntax. Bear in mind the following analogies:

| Tool               | Ruby          | JavaScript     |
| ------------------ | ------------- | -------------- |
| REPL               | `irb`         | `node`         |
| Package Repository | Rubygems.org  | npmjs.com      |
| Package Manager    | `bundle`      | `yarn`         |
| Project File       | `Gemfile`     | `package.json` |
| Linter             | Rubocop       | Eslint         |
| Test Framework     | Rspec         | Jest           |


## JavaScript <a name="js"></a>
### Introduction <a name="introduction"></a>
Modern JavaScript (JS) is ES6.
To launch a JS file:
```bash
node hello_world.js
```
In ES6 `var` is no longer used

`let`  is used. The variable can change. `let` is block scoped ie. referenced only in curly brackets, so only stays where declared.
If want to use outside then use outside before function scope.
So its more intuitive.

`const` is used when you dont want the variable to change. Hence, more restrictive.
Always start with `const`

So why do we use JS? Speed of the brwser is the main reason. Pushing 100s of files just slows up the browser.

Just as Asset pipleline helps rails.
JS client side uses webpack as a tool to do this.
Both npm and yarn are used to fetch dependencies fron internet.
