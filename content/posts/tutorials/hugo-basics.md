---
title: "Creating a website with hugo"
date: 2021-05-01
categories:
  - tutorial
draft: false
---

{{< reveal "http://christophernegrich.com/reveal-slides/slides/using-hugo.html" >}}

## How to create a website using hugo
---

### How this site is built
This site is built using [hugo](https://gohugo.io/). Hugo is a framework for building static html from [markdown](https://www.markdownguide.org/) pages, a theme, and a configuration file for the theme. Markdown is relatively easy to understand and much friendlier to users than html. The configuration file is just a text file containing settings and the theme is some prebuilt html and javascript.

### How to use Hugo

First, you will need to install hugo. A full guide is available [here](https://gohugo.io/getting-started/installing). But briefly, to install hugo just use a package manager for your operating system. On mac os, this is brew, on linux, apt or pacman or brew or snap or etc., on windows this means chocolatey or scoop. Each of these package managers is a command line utility. Essentially just open the terminal or powershell and type ```[package manager] install hugo``` for instance ```brew install hugo```. You can also install by downloading the tarball, which is a compressed folder containing all of the files.  

Once you have installed hugo, you can get started. The first step is to create the basic site. Hugo provides a command to generate most of the basic files that you will need: ```hugo new site [site_name]``` for instance ```hugo new site resume-site```. Now go choose a [theme](https://themes.gohugo.io/). Once you have your theme, turn your site into a git repository with ```cd [site_name] && git init```. Then add the theme as a submodule with ```git submodule [theme git link]``` for instance ```git submodule https://themes.gohugo.io/hugo-theme-hello-friend-ng/ themes/hello-friend-ng```. Hello-friend-ng is the theme for this site. Be a little careful with this submodule command. I added ``` themes/hello-friend-ng``` to the end of my command to change the name of the theme from hugo-theme-hello-friend-ng to hello-friend-ng. You may want to do this if the repository has a different name than the theme.  I only made slight modifications. Now, open your config.toml file in any file editor and add the line ```theme = theme_name``` or in my case ```theme = hello-friend-ng```. You can make further edits as desired here. This file is just a long settings file and can contain as much or little information as you would like. Each theme will have some different options here, so read the documentation for your theme to figure out what you would like to change. My config.toml is available [here](https://github.com/cnegrich/cnegrich.github.io/blob/master/config.toml). There are a few settings that I will draw attention to before continuing. First, you should add a site title and author:

```
title        = "Christopher Negrich"
[author]
    name = "Christopher Negrich"
```

Second, the base url is important:
```
baseurl      = "/"
```
By default, this will be set to ```"localhost"``` which just means that the base url is your local system. If you change this to ```"/"``` immediately, you may experience some trouble in viewing your site on your computer. However, before committing the final site, you will need to change this base url to allow the site to be hosted at your desired domain. I made the change right away and did not experience any difficulties in doing so, however I have in the past.

Now that the site has a theme and the basic files, you can view it. To view the site locally (on your machine), just run ```hugo server -D```. This command will start a live server and host your site only on your machine. Since the sever is live, after each change you make to the files, the site will automatically update. This will let you view your site as you make it. The ```-D``` flag that I added will build files marked as drafts. Hugo lets you mark files as drafts. Files marked as drafts will not build unless you tell hugo to build them. This is convenient for letting some files be works in progress while you continue to add more content to your site. After running this command, hugo will give you an address to view your site, for example ```localhost:1313```. Just paste that address into any internet browser to view the site. After navigating to that address, you should see your new homepage.

Finally, to add content. So far, we have only made a homepage. Hugo has a command to help you with this. You can run ```hugo new posts/my-first-post.md```. Which will generate a new post based on your Default.md file within the archetypes file. You can edit this default file to generate posts with some default content such as formatting if you would like to. After opening the newly generated my first-post.md, you will notice some code at the top:
```
---
title: "My First Post"
date: 2019-03-26T08:47:11+01:00
draft: true
---
```
This is some more settings that hugo and your theme are aware of. You can modify this as needed. Changing draft to false will tell hugo to always build the page. When kept as true, the page will only be built when hugo is also building drafts. The date and time format can be changed based on your site's config.toml. Additional parameters can be added here as long as they are used by the theme or your site in some way. Aside from that, this is just a markdown file to type in. The markdown will be rendered into html by hugo when the site is built.

You can view my content's src code [here](https://github.com/cnegrich/cnegrich.github.io/tree/master/content/posts) for some examples.

### Advanced: Integrating RevealJS

There are some advanced features on this site. I modified the theme slightly to better fit my needs and integrate reveal js. Each of these posts has an embedded slide show at the top. To embed this slide show, I just add the following code into the markdown file:
```
{{< reveal "http://christophernegrich.com/reveal-slides/slides/using-hugo.html" >}}
```
Markdown allows for html to be added, however the above is different. Although markdown allows for arbitrary html, hugo will not know how to handle it. To add the desired html, I made a hugo [shortcode](https://gohugo.io/templates/shortcode-templates/). This was actually easier than I expected. There are a bunch of hugo shortcodes available on install, but I added a custom one for the slide show into  the layouts/shortcodes directory within my site [files](https://github.com/cnegrich/cnegrich.github.io/tree/master/layouts/shortcodes). Here is the shortcode template in its entirety:
```html
<div class="embed reveal-slides">
  <p align="center">
    <iframe class="reveal-js" type="text/html" width="640" height="385"
        src="{{ index .Params 0 }}" allowfullscreen frameborder="0">
    </iframe>
  </p>
</div>
```
The shortcode is just the html that I wanted to add into the markdown file. The only difference is the ```src="{{ index .Params 0 }}"``` which takes in the parameter from the markdown file. Now by calling the name of the shortcode, reveal, and passing in a parameter, a url to the src file, I can integrate reveal js into my posts. 

## External Links

---

### Hugo Documentation

[Hugo Docs](https://gohugo.io/documentation/)

### Email

[christopher.a.negrich@gmail.com](mailto:christopher.a.negrich@gmail.com)

### LinkedIn

[Christopher Negrich](https://www.linkedin.com/in/christopher-negrich)

### Github

[cnegrich](https://github.com/cnegrich)


### Twitter

[ChrisNegrich](https://twitter.com/ChrisNegrich)