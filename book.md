# Thank you!

Thanks for being interested enough in *Theming with Ghost* to buy it!

I'm excited to document the process of building themes for Ghost, and your support helps make that possible.

If you could share [themingwithghost.com](http://themingwithghost.com) with others interested in building Ghost themes, that would be wonderful.

## A book in progress
This book is highly inspired by the [lean publishing model](https://leanpub.com/manifesto). I'm releasing the book early to get feedback from you, dear readers, so that together we can make the best book about Ghost theming possible.

I'll be releasing updates regularly up until the book is feature complete at v1.0.0. Help me determine what it will mean for a book to be feature complete by emailing me at hi@learnjs.io to let me know what parts of Ghost theming you need to learn about most.

## This book is open source
Find errors or have ideas for improvements? Please send me an email at hi@learnjs.io or submit an issue at the issue queue for this book's GitHub repository: [github.com/learn-js/theming-with-ghost/issues](https://github.com/learn-js/theming-with-ghost/issues).


# Introduction


## About Ghost

Ghost is an exciting new blogging platform that focuses on creating beautiful writing & reading experience. Ghost is built on Node.js and Express.js, and a number of other modern web development tools.

Promoted as "just a blogging platform," there's already an active community of developers and designers forming around Ghost.

Creating simple, beautiful themes is a wonderful goal, and one that Ghost makes easy.


## About the book

### With this book you'll learn about:
- Setting up your computer for Ghost
- Introduction to Ghost theming & the Handlebars templating language
- Theme example: a landing page & blog theme focused on selling a product
- Developing Ghost themes with Yeoman, Grunt, and SASS
- Theme example: a picture-focused blog for your awesome photos
- Developing Ghost themes with browserify, myth, & other modules from npm
- Theme example: A minimalistic & clean, typography-focused blog theme

You'll receive the source code for the 3 theme examples, which will help you get started making different kinds of themes.


## About the author

Seth Vincent writes code, stories, and music. He's an independent programmer, designer and writer focused on storytelling and javascript. Seth works on [crtrdg.js](http://crtrdg.com), a toolkit for making 2d games with javascript, [generator-ghost](http://github.com/sethvincent/generator-ghost), a Yeoman generator for Ghost, [The Owl](http://superbigtree.com/themes/the-owl), a theme for Ghost, [ghost-skeletheme](http://github.com/sethvincent/ghost-skeletheme), a starter theme for Ghost, and is writing a series of books about JavaScript called *Learn.js* that you can learn about at [learnjs.io](http://learnjs.io). He's a co-organizer of [seattle.io](http://seattle.io) and [Code for Seattle](http://codeforseattle.org), and owner of [Super Big Tree](http://superbigtree.com). Find Seth on [github](http://github.com/sethvincent) and [twitter](http://twitter.com/sethdvincent).


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

```
git clone https://github.com/creationix/nvm.git ~/.nvm
```

Source nvm to make it the `nvm` command available in the terminal:

```
source ~/.nvm/nvm.sh
```

To ensure that `nvm` is available at all times in the terminal, add the above line to your ~/.bashrc file:

```
nano ~/.bashrc
```

To get the `nvm` command after adding that line to your ~/.bashrc file, source your ~/.bashrc file:

```
source ~/.bashrc
```

To ensure `nvm` is working, run the command without options:

```
nvm
```

You should see output like this:

```
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
```

The above help text gives a good overview of usage of the `nvm` command.


### Now install node.js with `nvm`

Install the latest version of node v0.10.x:

```
nvm install 0.10
```

You'll see output like this:

```
######################################################################## 100.0%
Now using node v0.10.21
```

We can switch to that new version using this command:

```
nvm use 0.10.21
```

And to set that version as the default, set the default alias:

```
nvm alias default 0.10.21
```


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


# Ghost themes and Handlebars

## Basics of Handlebars

Ghost uses a templating language named Handlebars.

Template tags look like this:

```
{{title}}
```

Here's an example snippet of a blog post template:

```
<article class="post">
  <h1 class="post-title">
    {{title}}
  </h1>
  <div class="post-content">
    {{content}}
  </div>
</article>
```

If the post title is "Pizza is awesome!" and the post content is "I'm serious, it's really great." the generated HTML will look like this:

```
<article class="post">
  <h1 class="post-title">
    Pizza is awesome!
  </h1>
  <div class="post-content">
    I'm serious, it's really great.
  </div>
</article>
```

### Learn more about Handlebars

To get a quick run-through of using Handlebars, check out the Handlebars website: [handlebarsjs.com](http://handlebarsjs.com/)


## Get started by copying & inspecting the Casper theme

Let's get started by making a copy of the Casper theme, Ghost's default theme, and making some revisions.

Navigate to the `content/themes` directory of your Ghost blog using the terminal:

```
cd your-ghost-blog/content/themes
```

Copy the entire Casper folder:

```
cp -R casper pizza
```

The `-R` option copies all the files in the folder recursively. I called my new theme `pizza`, you can call yours whatever you like.


## Switching themes

You can switch the theme your Ghost blog uses by following these instructions:

- Place a new theme in the content/themes directory of your blog
- Restart your Ghost server
- Login to the admin section of your blog at the `http://127.0.0.1:2368/ghost` url
- Navigate to `http://127.0.0.1:2368/ghost/settings/general` in your browser
- Select the name of your new theme from the **Theme** options dropdown.
- Click **Save**


## Files and folder structure of a Ghost theme

Change directory into your new theme folder using the terminal:

```
cd pizza
```

If you didn't name your theme pizza, run `cd whatever-your-theme-name`.

To take a look at what's in the folder, run the `ls` command on the terminal:

```
LICENSE
README.md
assets
default.hbs
index.hbs
page.hbs
post.hbs
```

Only the `index.hbs` and `post.hbs` files are absolutely required for your theme to work. Your folders for images, css, JavaScript and fonts are required to be inside a directory named `assets`.

In this chapter we'll look at examples of these template files from Casper and Ghost core, and in the following chapters we'll explore each template in depth.

### default.hbs

The default.hbs file is the layout template that all other templates are rendered inside.

Here's the example from the Casper theme:

```
<!DOCTYPE html>
<html>
<head>
  {{! Document Settings }}
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />

  {{! Page Meta }}
  <title>{{meta_title}}</title>
  <meta name="description" content="{{meta_description}}" />

  <meta name="HandheldFriendly" content="True" />
  <meta name="MobileOptimized" content="320" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <link rel="shortcut icon" href="{{asset "favicon.ico"}}">

  {{! Styles'n'Scripts }}
  <link rel="stylesheet" type="text/css" href="{{asset "css/screen.css"}}" />
  <link rel="stylesheet" type="text/css" href="//fonts.googleapis.com/css?family=Noto+Serif:400,700,400italic|Open+Sans:700,400" />

  {{! Ghost outputs important style and meta data with this tag }}
  {{ghost_head}}
</head>
<body class="{{body_class}}">

  {{! Everything else gets inserted here }}
  {{{body}}}

  <footer class="site-footer">
    <a class="subscribe icon-feed" href="{{@blog.url}}/rss/"><span class="tooltip">Subscribe!</span></a>
    <div class="inner">
       <section class="copyright">All content copyright <a href="{{@blog.url}}/">{{@blog.title}}</a> &copy; {{date format="YYYY"}} &bull; All rights reserved.</section>
       <section class="poweredby">Proudly published with <a class="icon-ghost" href="http://ghost.org">Ghost</a></section>
    </div>
  </footer>

  {{! Ghost outputs important scripts and data with this tag }}
  {{ghost_foot}}

  {{! The main JavaScript file for Casper }}
  <script type="text/javascript" src="{{asset "js/jquery.fitvids.js"}}"></script>
  <script type="text/javascript" src="{{asset "js/index.js"}}"></script>

</body>
</html>
```

### Global settings for your blog

Anywhere in your templates you can use the following template tags that output whatever settings you configured in the Ghost admin dashboard and in config.js:

**The blog url for the current environment:**

```
{{@blog.url}}
```

This is set in the `config.js` file.

The rest of these are configured from the settings page:

**The blog title:**

```
{{@blog.title}}
```

**The blog description:**

```
{{@blog.description}}
```

**The blog logo:**

```
{{@blog.logo}}
```

### Global helpers

**The body class:**

```
{{body_class}}
```

Add the body_class tag to your html body tag like so:

```
<body class="{{body_class}}">
```

Here are the tags that are ouput by the body_class tag:

**On the front page:**

```
home-template
```

**On post pages:**

```
post-template
```

If the post is actually a static page it'll have the `page` class.

And if it has any tags, it'll have a class for each tag, starting with `tag-`.

**When navigating older posts using pagination:**

```
archive-template
```


**The ghost_head:**

```
{{ghost_head}}
```

The ghost_head tag outputs meta tags, styles, and more. It's meant for placing in the `<head>` section of your template.


**The ghost_foot:**

```
{{ghost_foot}}
```

The ghost_foot tag is for outputting JavaScript files. By default it adds jQuery to the page. It should be placed just before the closing `</body>` tag in your template.

**The meta_title:**

```
{{meta_title}}
```

If the current page is the front page, the meta_title will output the blog title. If you're currently viewing a post, it'll output the post title.

This is meant for the `<title>` tag in the `<head>` section. Like this:

```
<title>{{meta_title}}</title>
```
**The meta_description:**

```
{{meta_description}}
```

Similar to the meta_title tag, the meta_description tag shows the blog description on all pages except post pages. Currently it does not output anything on post pages. It should be used for populationg the description meta tag like this:

```
<meta name="description" content="{{meta_description}}" />
```


### index.hbs

The index.hbs file is shown when you navigate to the front page of your Ghost blog.

Here's an example from the Casper theme:

```
{{!< default}}

{{! The comment above "< default" means - insert everything in this file into
    the {body} of the default.hbs template, which contains our header/footer. }}

{{! The big featured header on the homepage, with the site logo and description }}
<header class="site-head" {{#if @blog.cover}}style="background-image: url({{@blog.cover}})"{{/if}}>
  <div class="vertical">
    <div class="site-head-content inner">
      {{#if @blog.logo}}<a class="blog-logo" href="{{@blog.url}}"><img src="{{@blog.logo}}" alt="Blog Logo" /></a>{{/if}}
      <h1 class="blog-title">{{@blog.title}}</h1>
      <h2 class="blog-description">{{@blog.description}}</h2>
    </div>
  </div>
</header>

{{! The main content area on the homepage }}
<main class="content" role="main">

  {{! Each post will be output using this markup }}
  {{#foreach posts}}

  <article class="{{post_class}}">
    <header class="post-header">
      <span class="post-meta"><time datetime="{{date format='YYYY-MM-DD'}}">{{date format="DD MMM YYYY"}}</time> {{tags prefix="on "}}</span>
      <h2 class="post-title"><a href="{{url}}">{{{title}}}</a></h2>

    </header>
    <section class="post-excerpt">
      <p>{{excerpt}}&hellip;</p>
    </section>
  </article>

  {{/foreach}}

  {{!! After all the posts, we have the previous/next pagination links }}
  {{pagination}}

</main>
```

Note the `{{!< default}}` tag. This ensures that the current template is rendered inside the `default.hbs` layout template.

To get a list of posts you'll use a `{{#foreach}}` tag. Here's an extra simple example that prints every post title in an h2 tag:

```
{{#foreach posts}}
  <h2>{{title}}</h2>
{{/foreach}}
```

Pagination is added by using the `{{pagination}}` tag.



### post.hbs

When viewing a blog post, the post.hbs file is what is rendered.

Here's an example from the Casper theme:

```
{{!< default}}

{{! The comment above "< default" means - insert everything in this file into
    the {body} of the default.hbs template, which contains our header/footer. }}

<main class="content" role="main">

  <article class="{{post_class}}">

    {{! Each post has the blog logo at the top, with a link back to the home page }}
    <header class="post-header">
      <a class="blog-logo" href="{{@blog.url}}">
        {{#if @blog.logo}}
          <img src="{{@blog.logo}}" alt="Blog Logo" />
        {{else}}
          <span class="blog-title">{{@blog.title}}</span>
        {{/if}}
      </a>
    </header>

    {{! Everything inside the #post tags pulls data from the post }}
    {{#post}}

      <span class="post-meta"><time datetime="{{date format="YYYY-MM-DD"}}">{{date format='DD MMM YYYY'}}</time> {{tags prefix="on " separator=" | "}}</span>

      <h1 class="post-title">{{{title}}}</h1>

      <section class="post-content">
          {{content}}
      </section>

      <footer class="post-footer">

        <section class="author">
          <h4>{{author.name}}</h4>
          <p>{{author.bio}}</p>
        </section>

        <section class="share">
          <h4>Share this post</h4>
          <a class="icon-twitter" href="http://twitter.com/share?text={{encode title}}&url={{url absolute="true"}}"
              onclick="window.open(this.href, 'twitter-share', 'width=550,height=235');return false;">
              <span class="hidden">Twitter</span>
          </a>
          <a class="icon-facebook" href="https://www.facebook.com/sharer/sharer.php?u={{url absolute="true"}}"
              onclick="window.open(this.href, 'facebook-share','width=580,height=296');return false;">
              <span class="hidden">Facebook</span>
          </a>
          <a class="icon-google-plus" href="https://plus.google.com/share?url={{url absolute="true"}}"
             onclick="window.open(this.href, 'google-plus-share', 'width=490,height=530');return false;">
              <span class="hidden">Google+</span>
          </a>
        </section>

      </footer>

    {{/post}}

  </article>

</main>
```

### post properties
Here are all the possible post properties you can include in the post.hbs template:

**The post id:**

```
{{id}}
```

**The post title:**

```
{{title}}
```

**The relative url of a post:**

```
{{url}}
```

**The post HTML content:**

```
{{content}}
```

**The date the post was published:**

```
{{published_at}}
```

### The post class

To add a unique class to each post, use the post_class tag:

```
{{post_class}}
```

You should add it to the container element for the post. The Casper theme uses post_class like this:

```
<article class="{{post_class}}">
  ... all the post html ...
</article>
```

### Author details

In post and page templates you can access the author object to print details about the content author.

**Author name:**

```
{{author}}
```

or

```
{{author.name}}
```

**Author email address:**

```
{{author.email}}
```

**Author bio:**

```
{{author.bio}}
```

**Author website:**

```
{{author.website}}
```

**Author profile image:**

```
{{author.image}}
```

**Author cover image:**

```
{{author.cover}}
```

You can also use a block expression to access the properties on the author object:

```
{{#author}}
  <h3 class="author-name">
    {{name}}
  </h3>
  <div class="author-bio">
    {{bio}}
  </div>
{{/author}}
```

As you can see, the block expression allows you to access properties like the name and bio of the author with a more concise syntax.


### page.hbs

The page.hbs file is very similar to the post.hbs file, except it is meant for static pages rather than timestamped posts. If your theme doesn't have a page.hbs file Ghost will fall back to using the post.hbs template for static pages.

Here's an example page.hbs file from the Casper theme:

```
{{!< default}}

{{! This is a page template. A page outputs content just like any other post, and has all the same
    attributes by default, but you can also customise it to behave differently if you prefer. }}

<main class="content" role="main">

  <article class="{{post_class}}">

    <header class="post-header">
      <a class="blog-logo" href="{{@blog.url}}">
        {{#if @blog.logo}}
          <img src="{{@blog.logo}}" alt="Blog Logo" />
        {{else}}
          <span class="blog-title">{{@blog.title}}</span>
        {{/if}}
      </a>
    </header>

    {{#post}}

      <h1 class="post-title">{{{title}}}</h1>

      <section class="post-content">
        {{content}}
      </section>

    {{/post}}

  </article>

</main>
```

### assets

The assets directory is where you'll store the css, javascript, images, and fonts that you use in your theme.

The directory structure looks like this:

```
assets/css
assets/fonts
assets/images
assets/js
```

Assets are automatically compiled by Ghost and made accessible in your templates with the `{{asset}}` helper.

A brief look at the `{{asset}}` helper:

If you have an image named `pizza.jpg` in your `assets/images` folder you want to use in your theme, you can access with this tag:

```
{{asset images/pizza.jpg}}
```

JavaScript, CSS, and other files work the same way.

The `favicon.ico` file is a little different.

This serves the default Ghost favicon:

```
{{asset "favicon.ico"}}
```

**To override that and add your own favicon, do the following:**

1. Place your own favicon in the  `assets/images/` folder.
2. Use the asset tag with a leading slash, like this:

```
{{asset "/images/favicon.ico"}}
```

The leading slash indicates that Ghost should look in the assets folder of your theme rather than using the favicon that's part of core Ghost.

### LICENSE and README.md
Neither the LICENSE file or the README.md are required in a technical sense, but they are definitely necessary if you're developing a theme that you'll be releasing for others to use.

### error.hbs

Not included in Casper is the error.hbs file, an optional template that will be shown when users get a 404 or other server error.

Here's the example of the error.hbs that is used in core Ghost:

```
{{!< default}}
<section class="error-content error-404 js-error-container">
    <section class="error-details">
        <figure class="error-image">
            <img class="error-ghost" src="{{asset "img/404-ghost@2x.png" ghost="true"}}" srcset="{{asset "img/404-ghost.png" ghost="true"}} 1x, {{asset "img/404-ghost@2x.png" ghost="true"}} 2x"/>
        </figure>
        <section class="error-message">
            <h1 class="error-code">{{code}}</h1>
            <h2 class="error-description">{{message}}</h2>
        </section>
    </section>
</section>
{{#if stack}}
    <section class="error-stack">
        <h3>Stack Trace</h3>
        <p><strong>{{message}}</strong></p>
        <ul class="error-stack-list">
            {{#foreach stack}}
                <li>
                    at
                    {{#if function}}<em class="error-stack-function">{{function}}</em>{{/if}}
                    <span class="error-stack-file">({{at}})</span>
                </li>
            {{/foreach}}
        </ul>
    </section>
{{/if}}
```

If you don't include an error.hbs file in your theme, this default template is used. 

## Partials

You can use partials in your templates using a tag like the following:

`{{> name-of-partial}}`

You'll need to create a `partials` directory in your theme where you'll store all your partials.

### Adding new partials

Let's say you want a partial for a sidebar. Create a `sidebar.hbs` file in your theme's `partials` folder.

Give the `sidebars.hbs` file some content:

```
<section id="sidebar">
  <h1 class="sidebar-title">
    Important sidebar!
  </h1>
  <div class="sidebar-content">
    Important content in the sidebar!
  </div>
</section>
```

Now to use the sidebar in one of your templates, include it with the following tag:

```
{{> sidebar}}
```

### Overriding partials

To override a partial, create a file of the same name as the partial you want to override in your partials folder.

Here are a few partials you might consider overriding:

- pagination.hbs – it's located at `your-ghost-blog/core/server/helpers/tpl/pagination.hbs

This list will get longer as new functionality is introduced to Ghost.


# Theme example: a landing page & blog theme focused on selling a product

It's time for the first theme example! The goal for this chapter is to create a theme that acts as a landing page and blog for a product. We'll use the site I developed for this book, [themingwithghost.com](http://themingwithghost.com) as an example for this theme.

Note that it will be a very bare-bones theme. Something you can use as a starting point to customize and give a style of your own. It'll act as an introduction to Ghost templates, not so much the details of CSS.

You'll find the full source code theme in the download you received after purchasing the book.

## Create the files and folders

```
cd your-ghost-blog/content/themes
```

```
mkdir landing-page
```

```
mkdir -p assets/css assets/js assets/images partials
```

```
touch default.hbs index.hbs post.hbs
```

```
touch assets/css/style.css assets/js/index.js
```


## Create a default layout

In the default.hbs file add this content:

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <title>{{meta_title}}</title>
  <meta name="description" content="{{meta_description}}" />
  <meta name="HandheldFriendly" content="True" />
  <meta name="MobileOptimized" content="320" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link rel="shortcut icon" href="{{asset "favicon.ico"}}">
  <link href='http://fonts.googleapis.com/css?family=Lora:400,400italic|Open+Sans:300,700' rel='stylesheet' type='text/css'>
  <link rel="stylesheet" type="text/css" href="{{asset "css/style.css"}}" />

  {{ghost_head}}
</head>
<body class="{{body_class}}">

  <header class="site-header" {{#if @blog.cover}}style="background-image: url({{@blog.cover}})"{{/if}}>
    <div class="container">
      <div class="logo-and-title">
        {{#if @blog.logo}}
          <a class="blog-logo" href="{{@blog.url}}">
            <img src="{{@blog.logo}}" alt="Blog Logo" />
          </a>
        {{/if}}
        <h1 class="blog-title">
          <a href="{{@blog.url}}">
            {{@blog.title}}
          </a>
        </h1>
      </div>
      <div class="blog-description">{{@blog.description}}</div>
    </div>
  </header>

  <main class="site-content" role="main">
    <div class="container">
      {{{body}}}
    </div>
  </main>

  <footer class="site-footer">
    <div class="container">
      <section class="copyright">
      	All content copyright 
      	<a href="{{@blog.url}}/">
      		{{@blog.title}}
      	</a> &copy; {{date format="YYYY"}} &bull; 
      	All rights reserved.
      </section>
    </div>
  </footer>

  {{ghost_foot}}

  <script type="text/javascript" src="{{asset "js/index.js"}}"></script>
</body>
</html>
```

## Add content to index.hbs

Add this content to your `index.hbs` file:

```
{{!< default}}

<div id="static-content">

	<div class="banner">
	  <h1 class="post-title">
	    You're selling a product, so you better show what problem it's solving in your first big header.
	  </h1>

	  <p><a href="#" class="button buy">Buy the thing</a></p>
  </div>

  <section class="about">
    <h1>About the problem you're solving</h1>
    <p>Give a brief amount of background on the problem you're solving</p>
  </section>

  <section class="about">
    <h1>About how your product is awesome</h1>
    <p>Give a brief amount of inspiration to buy the product</p>
  </section>  

  <section class="about">
    <h1>About the company/author/organization</h1>
    <p>Add some text about who you are.</p>
  </section>

</div>

<section id="posts">
  {{#if posts}}
    <h1 class="center-text">Our recent posts about the thing:</h1>
    {{#foreach posts}}
      <article class="{{post_class}}">
        <h3 class="post-title"><a href="{{url}}">{{{title}}}</a></h3>
      </article>
    {{/foreach}}
    {{pagination}}
    <hr>
  {{/if}}
</section>
```

Clearly this is a very basic implementation of a front page, and you'll want to add all the details necessary for your product.

## Create a product partial

Make the partial file:

```
touch partials/product.hbs
```

Add content similar to this to your `product.hbs` file:

```
<section id="product">
  <h1 class="product-title">
    The Thing
  </h1>
  <div class="product-description">
    <p>Your description of how great the thing is and how it fits into the life of your customers.</p>
  </div>
  <p><a href="#" class="button buy">Buy the thing</a></p>
</section>
```

You can now include the `product` partial in other templates:

```
{{> product}}
```

## Create a share partial

To help keep our post.hbs file from getting cluttered, let's add the html for sharing posts to a partial.

Make the partial file:

```
touch partials/share.hbs
```

Add this content to the `share.hbs` file:

```
<section class="share">
  <b>Share this post:</b> 
  <a class="icon-twitter" href="https://twitter.com/share?text={{encode title}}&url={{url absolute="true"}}"
    onclick="window.open(this.href, 'twitter-share', 'width=550,height=235');return false;">
    <span class="hidden">Twitter</span>
  </a>
  <a class="icon-facebook" href="https://www.facebook.com/sharer/sharer.php?u={{url absolute="true"}}"
    onclick="window.open(this.href, 'facebook-share','width=580,height=296');return false;">
    <span class="hidden">Facebook</span>
  </a>
  <a class="icon-google-plus" href="https://plus.google.com/share?url={{url absolute="true"}}"
    onclick="window.open(this.href, 'google-plus-share', 'width=490,height=530');return false;">
    <span class="hidden">Google+</span>
  </a>
</section>
```

## Create a post.hbs template

Add this content to the `post.hbs` file:

```
{{!< default}}

<article class="post {{post_class}}">
  {{#post}}
    <h1 class="post-title">{{{title}}}</h1>
    <div class="post-meta">
      <time datetime="{{date format="YYYY-MM-DD"}}">
        {{date format='DD MMM YYYY'}}
      </time>
      {{tags prefix="on " separator=" | "}}
      :: <span class="accent">by</span> {{author.name}}
    </div>

    <section class="post-content">
      {{content}}
    </section>

    <footer class="post-footer">

      <section class="author-bio">
        <p>{{author.bio}}</p>
      </section>

      {{> share}}

    </footer>

  {{/post}}
</article>

{{> product}}
```

Note that I'm adding the product partial to the bottom of the `post.hbs` template so that people will be prompted to learn more about or buy your product after reading a post.

## Add css styles

These css styles will get your theme started. I've tried to add as many of the classes and ids that are typically used, and worked to follow a standard naming convention based on what you'll see in the Casper theme.

The following css includes basic media query examples for responsive design and 

```
/*
* BASE
*/

html,
body,
input,
button,
select,
textarea {
  font-size: 20px;
  line-height: 1.6;
  font-family: Georgia, serif;
  font-smoothing: antialiased;
  font-weight: 300;
  color: #444;
}

*,
*:before,
*:after {
  box-sizing: border-box;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: 'Helvetica Neue', Helvetica, sans-serif;
  text-rendering: optimizeLegibility;
  line-height: 1.2;
  margin-top: 0px;
  margin-bottom: 5px;
}

h1 {
  font-weight: 300;
}

a {
  color: #3c80c3;
  transition: all ease 0.2s;
  text-decoration: none;
}

a:hover {
  color: #57A3E8;
}

a:active,
a:focus {
  color: #1e4062;
}

p {
  margin-top: 5px;
  margin-bottom: 10px;
}

code {
  font-family: Monaco, Menlo, monospace;
  padding: 5px 10px;
  background-color: #fdfdfb;
  border: 1px solid #dadad8;
  font-size: 13px;
  border-radius: 2px;
  white-space: nowrap;
}

pre {
  font-family: Monaco, Menlo, monospace;
  font-size: 13px;
  padding: 10px 15px;
  background-color: #fdfdfb;
  border: 1px solid #dadad8;
  border-radius: 2px;
  overflow-x: auto;
  margin-bottom: 35px;
}

pre code {
  background-color: none;
  border: 0px;
  padding: 0px;
  white-space: pre;
}

hr {
  height: 1px;
  border: 0;
  border-top: 1px solid #efefef;
  margin: 30px 0 50px 0;
}

blockquote {
  font-family: 'Helvetica Neue', Helvetica, sans-serif;  
  font-size: 1.2em;
  border-left: 3px solid #efefef;
  padding: 0px 15px;
}

input,
textarea {
  border: 1px solid #efefef;
  padding: 6px 10px;
  font-family: 'Helvetica Neue', Helvetica, sans-serif;  
  border-radius: 2px;
}


/*
* BUTTON
*/

button, 
.button {
  font-family: 'Helvetica Neue', Helvetica, sans-serif;  
  display: inline-block;
  padding: 10px 15px 8px 15px;
  background-color: #3c80c3;
  border-radius: 3px;
  text-decoration: none;
  cursor: pointer;
  color: #fff;
  line-height: 1.7em;
}

button:hover, 
.button:hover {
  color: #fff;
  background-color: #57A3E8;
}


/*
* HEADER
*/

.site-header {
  text-align: center;
  margin: 40px 0px;
}

.logo-and-title {

}

.blog-logo {

}

.blog-title {
  font-weight: 900;
}

.blog-description {

}


/*
* MAIN
*/

.site-content {

}


/*
* FRONT PAGE
*/

#static-content {

}

/* hide the static content on archive pages */
.archive-template #static-content {
  display: none;
}

/* banner */

.banner {
  text-align: center;
}

.banner h1 {
  font-size: 1.8em;
  margin-bottom: 40px;
}

/* about sections */

.about {
  margin-top: 40px;
}

.about h1 {
}


/*
* POSTS
*/

/* the posts list */

#posts {

}

#posts h3.post-title {

}

/* individual posts */

.post {

}

.post-title {

}

.post-meta {

}

.post-content {

}

.post-content h1,
.post-content h2,
.post-content h3,
.post-content h4,
.post-content h5,
.post-content h6 {
  margin-top: 40px;
}

.post-content img {
  width: 100%;
  height: auto;
}

.post-footer {

}

.author-bio {

}


/*
* PAGINATION
*/

.pagination {
  font-size: 0.8em;
  font-family: 'Helvetica Neue', Helvetica, sans-serif; 
}


/*
* PRODUCT
*/

.product {
  margin-top: 50px;
  border-radius: 2px;
  padding: 15px 20px;
  background-color: #f2f2f0;
}

.product-title {
  font-size: 2.4em;
  font-weight: 900;
}

.product-description {
  font-size: 1.4em;
  font-family: 'Helvetica Neue', Helvetica, sans-serif; 
}


/*
* SHARE
*/

.share {
  font-family: 'Helvetica Neue', Helvetica, sans-serif; 
  font-size: 0.9em;
  margin-top: 20px;
  border-top: 1px solid #efefef;
  padding-top: 10px;
}

.twitter {

}

.facebook {

}

.google-plus {

}


/*
* FOOTER
*/

.site-footer {
  margin-top: 50px;
  border-top: 1px solid #efefef;
  padding-top: 10px;
}

.copyright {
  font-family: 'Helvetica Neue', Helvetica, sans-serif; 
  font-size: 0.8em;
  text-align: center;
}


/*
* LAYOUT
*/

/* mobile size */
.container {
  width: 100%;
  padding: 0px 10%;
  margin: 0px auto;
}

/* tablet size */
@media only screen and (min-width: 600px) {
  .container {
    width: 540px;
    padding: 0px 20px;
  }
}

/* desktop size */
@media only screen and (min-width: 960px) {
  .container {
    width: 800px;
  }
}
```


## Hide static content in index.hbs on archive pages

Remember the static content we added to the `index.hbs` file? One thing you'll notice is that that content will stick around on archive pages (when you navigate older posts through the pagination) unless you do something about it.

I'm using this CSS rule to hide that static content on the archive pages:

```
/* hide the static content on archive pages */
.archive-template #static-content {
  display: none;
}
```

These gives you a peek at how you can provide alternate content and styles depending on the page of your blog that is being viewed.


# This book is under active development

This book is a work in progress, and I'd love to get your feedback! Please email me at hi@learnjs.io to tell me about ideas you have for the book or issues you've discovered.

## A book in progress
This book is highly inspired by the [lean publishing model](https://leanpub.com/manifesto). I'm releasing the book early to get feedback from you, dear readers, so that together we can make the best book about Ghost theming possible.

I'll be releasing updates regularly up until the book is feature complete at v1.0.0. Help me determine what it will mean for a book to be feature complete by emailing me at hi@learnjs.io to let me know what parts of Ghost theming you need to learn about most.

## This book is open source
Find errors or have ideas for improvements? Please send me an email at hi@learnjs.io or submit an issue at the issue queue for this book's GitHub repository: [github.com/learn-js/theming-with-ghost/issues](https://github.com/learn-js/theming-with-ghost/issues).

## Share with others

If you could share [themingwithghost.com](http://themingwithghost.com) with others interested in building Ghost themes, that would be wonderful!


# v0.1.0 - February 10
- Added preface.md
- Added introduction.md
- Added installation.md
- Added ghost-templates-and-handlebars.md
- Added theme-example-landing-page.md
- Added source files for first version of landing page theme


