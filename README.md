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
    1. [React-Summary](#reactsummary)
    2. [New React Project](#reactproject)
    3. [New React App from Facebook](#reactappfacebook)
    4. [Deploy to github pages](#githubpages)
    5. [Simple react app and push to Prod](#simplereactpushtoprod)
    6. [Simple react app out of thebox](#simplereactappfb)
4. [React-Native](#reactnative)
    1. [Creating a new Native Application](#createnative)
    2. [Use a Virtual Android Device](#virtual)
    3. [Run the App](#runapp)
    4. [Time to Play](#play)
    4. [Simple Native App With Stylesheet](#simplenativeapp)
5. [Useful links](#links)
6. [Common Errors](#errors)
7. [Acknowledgements](#Acknowledgements)

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

### Downgrading to an older node
brew switch node 8.9.1
### Switch between versions of node
```bash
$ brew search node
$ brew install node@6
$ brew link node@6
```
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
[boilerplate](https://github.com/haseebc/JS_boiler_plate_from_scratch)
## React <a name="react"></a>
### React-Summary <a name="reactsummary"></a>
A component is responsible for producing one piece of HTML
Static data is carried by the component's props Mutable data is carried by the component's state State and events handling make interactivity possible
Stateless components can be coded as functions 
Stateful components need to be promoted as classes
Anytime a component's state changes (this.setState()), its render() method is called back
### New React Project <a name="reactproject"></a>

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
### New React App from Facebook <a name="reactappfacebook"></a>
New react app out of the box. From facebook.
```bash
yarn global add create-react-app
```
### Deploy to github pages <a name="githubpages"></a>
commit by doing the above
```bash
yarn deploy 
```
Then can browse to https://haseebc.github.io/react-gifs/
### Simple react app and push to Prod <a name="simplereactpushtoprod"></a>
Follow instructions here https://github.com/lewagon/react-redux-challenges/blob/master/02-Redux/01-React-Advanced/README.md
Use this solution https://github.com/lewagon/react-flats
```bash
yarn add gh-pages --dev
#add the module in your project
webpack -p
#create your production bundle
gh-pages -d dist 
https://haseebc.github.io/react-flats/
```
### Simple react app out of thebox <a name="simplereactappfb"></a>
```bash
yarn global add create-react-app
# gives you a create-react-app binary
create-react-app myfirstreactapp
# creates the app with a given configuration
yarn start
# Starts the development server.
```

## React-Native <a name="reactnative"></a>
### Creating a new Native Application <a name="createnative"></a>
```bash
npx react-native init AwesomeProject
#Create a new app
```

### Use a Virtual Android Device <a name="virtual"></a>
```bash
./AwesomeProject/android
#Open Android Studio into this directory
```

If you have recently installed Android Studio, you will likely need to create a new AVD. Select "Create Virtual Device...", then pick any Phone from the list and click "Next", then select the Q API Level 29 image.

### Run the App <a name="runapp"></a>
#### Step1 Start Metro 
First, you will need to start Metro, the JavaScript bundler that ships with React Native
```bash
npx react-native start
# Or if you prefer yarn
yarn react-native start
```
#### Step2 Start Your App <a name="startapp"></a>
```bash
npx react-native run-android
```

### Time to Play <a name="play"></a>
Modify your app using App.js, make changes and thats it! The first reactive native app setup!

### Simple Native App With Stylesheet <a name="simplenativeapp"></a>
#### Props
Most components can be customized when they are created, with different parameters. These creation parameters are called props.

Your own components can also use props. This lets you make a single component that is used in many different places in your app, with slightly different properties in each place. Refer to props.{NAME} in your functional components or this.props.{NAME} in your class components. Here's an example:

```bash
import React from 'react';
import { Text, View, StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  center: {
    alignItems: 'center'
  }
})

const Greeting = (props) => {
  return (
    <View style={styles.center}>
      <Text>Hello {props.name}!</Text>
    </View>
  );
}

const LotsOfGreetings = () => {
  return (
    <View style={[styles.center, {top: 50}]}>
      <Greeting name='Rexxar' />
      <Greeting name='Jaina' />
      <Greeting name='Valeera' />
    </View>
  );
}

export default LotsOfGreetings;
```
Using name as a prop lets us customize the Greeting component, so we can reuse that component for each of our greetings. This example also uses the Greeting component in JSX. The power to do this is what makes React so cool.

The other new thing going on here is the View component. A View is useful as a container for other components, to help control style and layout.

With props and the basic Text, Image, and View components, you can build a wide variety of static screens. To learn how to make your app change over time, you need to learn about State.

#### State
Unlike props that are read-only and should not be modified, the state allows React components to change their output over time in response to user actions, network responses and anything else.

***What's the difference between state and props in React?
In a React component, the props are the variables that we pass from a parent component to a child component. Similarly, the state are also variables, with the difference that they are not passed as parameters, but rather that the component initializes and manages them internally.***

Are there differences between React and React Native to handle the state?
There is no difference in handling the state between React and React Native. You can use the state of your components both in classes and in functional components using hooks!

In the following example we will show the same above counter example using classes.
```bash
import React, { Component } from 'react'
import {
  StyleSheet,
  TouchableOpacity,
  Text,
  View,
} from 'react-native'

class App extends Component {
  state = {
    count: 0
  }

  onPress = () => {
    this.setState({
      count: this.state.count + 1
    })
  }

 render() {
    return (
      <View style={styles.container}>
        <TouchableOpacity
         style={styles.button}
         onPress={this.onPress}
        >
         <Text>Click me</Text>
        </TouchableOpacity>
        <View>
          <Text>
            You clicked { this.state.count } times
          </Text>
        </View>
      </View>
    )
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
  button: {
    alignItems: 'center',
    backgroundColor: '#DDDDDD',
    padding: 10,
    marginBottom: 10
  }
})

export default App;
```
## Useful links <a name="links"></a>
https://babeljs.io/repl really useful for writing JS and seing what it looks like in JSX
https://reactnative.dev/docs/environment-setup setting up React Native 
https://reactnative.dev/docs/tutorial the best tutorial for ReactNative

## Common Errors <a name="errors"></a>
```bash
error Failed to install the app. Make sure you have the Android development environment set up
```
Fixed this issue by wipe data of the emulator. Go to android studio -> then open AVD Manager -> Click the triangle icon of the emulator. -> then click Wipe data. After that run react-native run-android 
## Acknowledgements <a name="Acknowledgements"></a>
I'd like to acknowledge the LeWagon bootcamp for its excellent course and support
