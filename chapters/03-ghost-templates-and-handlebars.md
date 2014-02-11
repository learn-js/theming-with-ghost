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