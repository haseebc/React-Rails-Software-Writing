# React-Rails-Software-Writing
# Table of contents
1. [Overview](#overview)
    1. [Setup](#setup)
    2. [Tools-Ruby-JS](#conclusion)
2. [Javascript](#js)
    1. [Introduction](#introduction)
    2. [New JS Project](#jsproject)
    3. [Boiler-plate](#jboilerplate)
3. [React](#react)
    1. [React in Summary](#reactsummary)
    2. [New React Project](#reactproject)
    3. [New React App from Facebook](#reactappfacebook)
4. [Useful links](#links)


## Overview
### Setup <a name="setup"></a>
⚠️ The purpose of these instructions is to give you a basic setup for the React environmnet. 🤓

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
### New JS Project <a name="jsproject"></a>
`filename yarn init `
add something from npm, say jquery
```bash
yarn add <package> [--dev]
yarn add jqury
```
Project files are in `packagae.json ` this is same as a Gemfile in rails.
`node_modules` contains the JS files.
`touch .gitignore`This is where you want to add the node_modules files because we dont want to commit and add this fie. Its huge so don't keep adding it
eslint helps write great code
In ruby quality of sytax is robocop. Its a gem but great to use to have nice code
```bash
yarn add eslint --dev
```
then run the following 
```bash
	eslint --init
	airbnb javascript style guide is great to use
	https://github.com/airbnb/javascript
	store file as json
```
### Boiler plate from scratch <a name="jboilerplate"></a>
    
## [React](#react)
### [React in Summary](#reactsummary)
A component is responsible for producing one piece of HTML
Static data is carried by the component's props Mutable data is carried by the component's state State and events handling make interactivity possible
Stateless components can be coded as functions 
Stateful components need to be promoted as classes
Anytime a component's state changes (this.setState()), its render() method is called back
### [New React Project](#reactproject)

Download boilerplate to new project `react-gifs` (or any other name)
```bash
cd ~/code/<github_username>
git clone git@github.com:lewagon/react-boilerplate.git react-gifs
cd react-gifs
yarn install
```
Destroy existing boilerplate git history, and start a new one
```bash
rm -rf .git
git init
git add .
git commit -m "Start new project from lewagon/react-boilerplate"
```
Create a GitHub repo, and push!
git remote add origin git@github.com:haseebc/react-gifs.git
git push -u origin master

Launch a webpack-dev-server and open a browser at http://localhost:8080!
or do yarn start
### [New React App from Facebook](#reactappfacebook)
New react app out of the box. From facebook.
```bash
yarn global add create-react-app
```


## [Useful links](#links)
https://babeljs.io/repl really useful for writing JS and seing what it looks like in JSX



