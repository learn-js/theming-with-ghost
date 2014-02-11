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