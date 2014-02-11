# Setting up your computer for Ghost
Installing and building sites on your local computer has a few dependencies, but as long as you can get Node.js installed, it's a pretty easy set-up process.


## Introduction to the terminal
For this book we'll be doing a great deal of work via the terminal, and there are a few basics you'll want to know. If you're familiar

For basics of using the terminal, see this chapter of the book Development Environments for Beginners: [Terminal: conquer the command line](https://github.com/sethvincent/dev-envs-book/blob/master/chapters/03-terminal.md)

Consider buying the Development Environments book here to learn more about setting up development environments: [learnjs.io/books/dev-envs](http://learnjs.io/books/dev-envs).


## Text editor
I recommend Sublime Text Editor for Windows, Mac, & Linux. It's a great editor, and you can try it for free before you buy it.

For basics of using Sublime, see this chapter of the book Development Environments for Beginners: [Text editors](https://github.com/sethvincent/dev-envs-book/blob/master/chapters/05-editors.md)


## Installing command-line tools

The most difficult part of getting started with a language isn't necessarily learning the syntax, data types, control structures, or other parts of the language itself. The hardest part is often learning the tools associated with the language's ecosystem. This tutorial provides a quick look at getting Node.js set up on your computer and using Node.js tools for both server and browser code.


## Installing git

[Git](http://git-scm.com) is version control software commonly used for open source projects in combination with [GitHub.com](http://github.com).

If you are using a Mac, you can install git using [homebrew](http://brew.sh/):

```
brew install git
```

> For more information about homebrew, check out the project's homepage: [brew.sh](http://brew.sh/).

On Debian/Ubuntu, install using apt-get:

```
apt-get install git
```

For Windows machines, download git from the git website: [git-scm.com/downloads](http://git-scm.com/downloads)


## Installing node.js

If you're on Windows, install node.js using the .msi package on the nodejs.org downloads page: [http://nodejs.org/downloads](http://nodejs.org/downloads).

If you're using Mac or Linux, I recommend using a tool called [nvm](https://github.com/creationix/nvm) for installing node.js if you're on mac or linux. It's very similar to the rbenv tool we used in the last chapter for installing ruby.


### If using `nvm`:

> If using Windows, please skip ahead to the "JavaScript in the Browser" section

We have git installed, so we can clone nvm to our home folder:

~~~~~~~~
git clone https://github.com/creationix/nvm.git ~/.nvm
~~~~~~~~

Source nvm to make it the `nvm` command available in the terminal:

~~~~~~~~
source ~/.nvm/nvm.sh
~~~~~~~~

To ensure that `nvm` is available at all times in the terminal, add the above line to your ~/.bashrc file:

~~~~~~~~
nano ~/.bashrc
~~~~~~~~

To get the `nvm` command after adding that line to your ~/.bashrc file, source your ~/.bashrc file:

~~~~~~~~
source ~/.bashrc
~~~~~~~~

To ensure `nvm` is working, run the command without options:

~~~~~~~~
nvm
~~~~~~~~

You should see output like this:

~~~~~~~~
Node Version Manager

Usage:
    nvm help                    Show this message
    nvm install [-s] <version>  Download and install a <version>
    nvm uninstall <version>     Uninstall a version
    nvm use <version>           Modify PATH to use <version>
    nvm run <version> [<args>]  Run <version> with <args> as arguments
    nvm ls                      List installed versions
    nvm ls <version>            List versions matching a given description
    nvm ls-remote               List remote versions available for install
    nvm deactivate              Undo effects of NVM on current shell
    nvm alias [<pattern>]       Show all aliases beginning with <pattern>
    nvm alias <name> <version>  Set an alias named <name> pointing to <version>
    nvm unalias <name>          Deletes the alias named <name>
    nvm copy-packages <version> Install global NPM packages contained in <version> to current version

Example:
    nvm install v0.4.12         Install a specific version number
    nvm use 0.2                 Use the latest available 0.2.x release
    nvm run 0.4.12 myApp.js     Run myApp.js using node v0.4.12
    nvm alias default 0.4       Auto use the latest installed v0.4.x version
~~~~~~~~

The above help text gives a good overview of usage of the `nvm` command.


### Now install node.js with `nvm`

Install the latest version of node v0.10.x:

~~~~~~~~
nvm install 0.10
~~~~~~~~

You'll see output like this:

~~~~~~~~
######################################################################## 100.0%
Now using node v0.10.21
~~~~~~~~

We can switch to that new version using this command:

~~~~~~~~
nvm use 0.10.21
~~~~~~~~

And to set that version as the default, set the default alias:

~~~~~~~~
nvm alias default 0.10.21
~~~~~~~~


## Javascript in the browser

You don't need to install anything for javascript in the browser. The browser takes care of that for you. I recommend using Chrome for the examples in this book. Firefox is also excellent, and if you choose to use it, there will be just slight differences between the developer tools compared to Chrome.

Download Chrome here: [https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

To get the most out of Chrome, become familiar with its built-in developer tools. The best resource for getting started is [Code School's Discover DevTools course](http://discover-devtools.codeschool.com/), a free interactive tutorial for learning the Chrome DevTools.

Also refer to the main documentation for chrome: [developers.google.com/chrome-developer-tools](https://developers.google.com/chrome-developer-tools/)


## Package manager: npm
When you install node.js, you get npm.

**npm:** [http://npmjs.org](http://npmjs.org)

You may also want to use [bower](http://bower.io/) or [component](http://component.io), two package managers that specifically target client-side code. Remember that javascript packages distributed via npm are not limited to node.js, and can also be used in the browser in many cases through the use of module bundlers like [browserify](http://browserify.org) and [webpack](http://webpack.github.io/).


# Downloading Ghost

## Downloading a zip file

You can download the latest build of Ghost from [ghost.org/download/](https://ghost.org/download/).

Click the **DOWNLOAD NOW** button button and save the zip file to your project folder on your computer.

Once the zip file has finished downloading to your computer, double click it to extract the files, or run a command like the following on the terminal:

```
unzip ghost-0.4.1.zip
```

## A Yeoman generator for Ghost

I created a [Yeoman](http://yeoman.io/) generator for the Ghost [generator-ghost](https://github.com/sethvincent/generator-ghost). You can optionally use it to download Ghost and begin working on a theme on your local computer.

Currently it will download Ghost and the default Casper theme. You can also copy the Casper theme over to a new folder with the `theme-copy-casper` subgenerator to get started on a customized theme.

### Install

Make sure you have the `yo` module installed:

```
npm install -g yo
```

Install generator-ghost:

```
npm install -g generator-ghost
```

### Usage

Create a directory for your ghost blog and enter that directory:

```
mkdir ghooooost && cd ghooooost
```

Run the ghost generator using `yo`:

```
yo ghost
```

This downloads Ghost and Casper.

To create a new theme based on Casper, run this subgenerator:

```
yo ghost:theme-copy-casper NAME-OF-NEW-THEME
```

That will copy the Casper theme over to a new folder named NAME-OF-NEW-THEME.

### Additional setup

Now, make sure you have the grunt-cli tool installed:

```
npm install -g grunt-cli
```

And run `grunt init` to compile the SASS, Handlebars, and create the directory for Bourbon:

```
grunt init
```

Now, you can run your ghost blog in development like usual:

```
npm start
```

### Feedback
Let me know in the repository issue queue if you find any bugs or have ideas for the project: [github.com/sethvincent/generator-ghost/issues](https://github.com/sethvincent/generator-ghost/issues)


# Run Ghost locally

We're going to make sure you can run Ghost locally on your computer now that you've downloaded it.

Navigate to the folder to which you downloaded Ghost:

```
cd path/to/your/ghost/blog
```

The directory should have these contents:

```
Gruntfile.js  
LICENSE  
README.md  
config.example.js  
content  
core  
index.js  
package.json  
```

If you haven't already, run this command on the terminal to install dependencies from npm:

```
npm install --production
```

If everything is working properly, you'll output like this:

```
Ghost is running in development... 
Listening on 127.0.0.1:2368 
Url configured as: http://my-ghost-blog.com 
Ctrl+C to shut down
```

You can now access your Ghost blog at the url `http://127.0.0.1:2368`. Go ahead and copy that into your browser and check it out!

### Configuring a development url

You'll notice that the above output says your url is `configured as http://my-ghost-blog`.

Let's fix that!

Open the `config.js` file with your text editor, and change this section:

```
config = {
    // ### Development **(default)**
    development: {
        // The url to use when providing links to the site, E.g. in RSS and email.
        url: 'http://my-ghost-blog.com',
```

So that the url is `http://127.0.0.1:2368`:

```
config = {
    // ### Development **(default)**
    development: {
        // The url to use when providing links to the site, E.g. in RSS and email.
        url: 'http://127.0.0.1:2368',
```

That way all links will work properly while developing your site.

If the development server that you started earlier is still running, open that terminal window and press the `control` key and the `C` key at the same time to shut down the server.

Start the server back up using `npm start` and you're ready to get started on your theme!