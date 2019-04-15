# Hugo Tuflove Theme

Edward Tufte uses a distinctive style in his handouts: simple, with well-set typography, extensive sidenotes, and tight integration of graphics and charts. This project brings Tufte style to Hugo with responsive navigation bars.

This project is directly inspired by and based on

* [Tufte CSS](https://github.com/edwardtufte/tufte-css) - The Tufte style sheet for HTML documents
* [W3.CSS](https://www.w3schools.com/w3css/) - A CSS framework with simple and beautiful navigation bars
* [Hugo](https://gohugo.io/) - The content management framework used

## How this template is built
This tutorial will show how to creat a simple theme in Hugo. The initial goals are very simple

* To make a blog template which supports Tufte style sidenotes.
* To add navigation bars to organize categories and topic groups.
* To automatically generate article indeces. 

I assume you are familliar with HTML, CSS, and Markdown. I'll mainly explain how templates serve as dynamic content processors in Hugo, and how to organize templates to form a theme.

## install Hugo
I'm a Mac user. So I'll use Homebrew to install Hugo. if you are using Window, Linux, or BSD operating systems, please refer to Hugo installation documents. Overall a quite easy step.

```
$ brew install hugo
$ hugo version
Hugo Static Site Generator v0.52/extended darwin/amd64 BuildDate: unknown
```

That's it. Hugo installation completed. 

## Create a new site
Let's use Hugo to create a new site. I creat mine in my project folder. 

```
$ hugo new site exampleSite
Congratulations! Your new Hugo site is created in /Users/mxu/Projects/Writing/hugo-tuflove-theme/exampleSite.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/, or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.

$ ls -l exampleSite/
total 8
drwxr-xr-x  3 mxu  staff  96 Apr 13 23:05 archetypes
-rw-r--r--  1 mxu  staff  82 Apr 13 23:05 config.toml
drwxr-xr-x  2 mxu  staff  64 Apr 13 23:05 content
drwxr-xr-x  2 mxu  staff  64 Apr 13 23:05 data
drwxr-xr-x  2 mxu  staff  64 Apr 13 23:05 layouts
drwxr-xr-x  2 mxu  staff  64 Apr 13 23:05 static
drwxr-xr-x  2 mxu  staff  64 Apr 13 23:05 themes
```

The content/ directory is used to store markdown format posts. It is empty for a new site.
The other directories are used when costomizing a theme. Please ignore them for now.

## Create new posts
Hugo has a command to generate a skeleton post. 

```
$ cd exampleSite/
$ hugo --verbose new post/first.md
INFO 2019/04/14 22:49:30 No translation bundle found for default language "en"
INFO 2019/04/14 22:49:30 Translation func for language en not found, use default.
INFO 2019/04/14 22:49:30 i18n not initialized; if you need string translations, check that you have a bundle in /i18n that matches the site language or the default language.
INFO 2019/04/14 22:49:30 Using config file: /Users/mxu/Projects/Writing/hugo-tuflove-theme/exampleSite/config.toml
INFO 2019/04/14 22:49:30 attempting to create "post/first.md" of "post" of ext ".md"
/Users/mxu/Projects/Writing/hugo-tuflove-theme/exampleSite/content/post/first.md created
```

Now we have created the first article named first.md in the post folder.
```
$ cat content/post/first.md
---
title: "First"
date: 2019-04-14T22:49:30-07:00
draft: true
---
```

## Generate HTML from Markdown for the new site
Running the `hugo` command with no options will read all the available content and thanslate them into HTML files. It will also copy everything that's not content to proper locations. 
```
hugo --verbose
INFO 2019/04/14 22:56:29 No translation bundle found for default language "en"
INFO 2019/04/14 22:56:29 Translation func for language en not found, use default.
INFO 2019/04/14 22:56:29 i18n not initialized; if you need string translations, check that you have a bundle in /i18n that matches the site language or the default language.
INFO 2019/04/14 22:56:29 Using config file: /Users/mxu/Projects/Writing/hugo-tuflove-theme/exampleSite/config.toml
Building sites … INFO 2019/04/14 22:56:29 syncing static files to /Users/mxu/Projects/Writing/hugo-tuflove-theme/exampleSite/public/
WARN 2019/04/14 22:56:29 Found no layout for "taxonomyTerm", language "en", output format "HTML": create a template below /layouts with one of these filenames: categories/terms.en.html.html, categories/list.en.html.html, categories/terms.html.html, categories/list.html.html, categories/terms.en.html, categories/list.en.html, categories/terms.html, categories/list.html, taxonomy/terms.en.html.html, taxonomy/list.en.html.html, taxonomy/terms.html.html, taxonomy/list.html.html, taxonomy/terms.en.html, taxonomy/list.en.html, taxonomy/terms.html, taxonomy/list.html, _default/terms.en.html.html, _default/list.en.html.html, _default/terms.html.html, _default/list.html.html, _default/terms.en.html, _default/list.en.html, _default/terms.html, _default/list.html
WARN 2019/04/14 22:56:29 Found no layout for "taxonomyTerm", language "en", output format "HTML": create a template below /layouts with one of these filenames: tags/terms.en.html.html, tags/list.en.html.html, tags/terms.html.html, tags/list.html.html, tags/terms.en.html, tags/list.en.html, tags/terms.html, tags/list.html, taxonomy/terms.en.html.html, taxonomy/list.en.html.html, taxonomy/terms.html.html, taxonomy/list.html.html, taxonomy/terms.en.html, taxonomy/list.en.html, taxonomy/terms.html, taxonomy/list.html, _default/terms.en.html.html, _default/list.en.html.html, _default/terms.html.html, _default/list.html.html, _default/terms.en.html, _default/list.en.html, _default/terms.html, _default/list.html
WARN 2019/04/14 22:56:29 Found no layout for "home", language "en", output format "HTML": create a template below /layouts with one of these filenames: index.en.html.html, home.en.html.html, list.en.html.html, index.html.html, home.html.html, list.html.html, index.en.html, home.en.html, list.en.html, index.html, home.html, list.html, _default/index.en.html.html, _default/home.en.html.html, _default/list.en.html.html, _default/index.html.html, _default/home.html.html, _default/list.html.html, _default/index.en.html, _default/home.en.html, _default/list.en.html, _default/index.html, _default/home.html, _default/list.html
INFO 2019/04/14 22:56:29 Found no layout for "404", language "en", output format "HTML": create a template below /layouts with one of these filenames: 404.html

                   | EN
+------------------+----+
  Pages            |  3
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0
```

The `--verbose` flag gives extra information that will be helpful when we build the template. Every line of the output that start with "INFO" or "WARN" is bpresent because we used that flag.

This command also generated a new public/ directory. Hugo copied all generated content there. 
```
$ ls -l public
total 16
drwxr-xr-x  3 mxu  staff   96 Apr 14 22:56 categories
-rw-r--r--  1 mxu  staff  468 Apr 14 22:56 index.xml
-rw-r--r--  1 mxu  staff  437 Apr 14 22:56 sitemap.xml
drwxr-xr-x  3 mxu  staff   96 Apr 14 22:56 tags
```

Hugo generated two xml files and two folders, but there is no HTML files.

## Test the new site
To serve the new site, start by running the `server` command.
```
hugo server --verbose
INFO 2019/04/14 23:03:57 No translation bundle found for default language "en"
INFO 2019/04/14 23:03:57 Translation func for language en not found, use default.
INFO 2019/04/14 23:03:57 i18n not initialized; if you need string translations, check that you have a bundle in /i18n that matches the site language or the default language.
INFO 2019/04/14 23:03:57 Using config file: /Users/mxu/Projects/Writing/hugo-tuflove-theme/exampleSite/config.toml
Building sites … INFO 2019/04/14 23:03:57 syncing static files to /
WARN 2019/04/14 23:03:57 Found no layout for "taxonomyTerm", language "en", output format "HTML": create a template below /layouts with one of these filenames: categories/terms.en.html.html, categories/list.en.html.html, categories/terms.html.html, categories/list.html.html, categories/terms.en.html, categories/list.en.html, categories/terms.html, categories/list.html, taxonomy/terms.en.html.html, taxonomy/list.en.html.html, taxonomy/terms.html.html, taxonomy/list.html.html, taxonomy/terms.en.html, taxonomy/list.en.html, taxonomy/terms.html, taxonomy/list.html, _default/terms.en.html.html, _default/list.en.html.html, _default/terms.html.html, _default/list.html.html, _default/terms.en.html, _default/list.en.html, _default/terms.html, _default/list.html
WARN 2019/04/14 23:03:57 Found no layout for "taxonomyTerm", language "en", output format "HTML": create a template below /layouts with one of these filenames: tags/terms.en.html.html, tags/list.en.html.html, tags/terms.html.html, tags/list.html.html, tags/terms.en.html, tags/list.en.html, tags/terms.html, tags/list.html, taxonomy/terms.en.html.html, taxonomy/list.en.html.html, taxonomy/terms.html.html, taxonomy/list.html.html, taxonomy/terms.en.html, taxonomy/list.en.html, taxonomy/terms.html, taxonomy/list.html, _default/terms.en.html.html, _default/list.en.html.html, _default/terms.html.html, _default/list.html.html, _default/terms.en.html, _default/list.en.html, _default/terms.html, _default/list.html
WARN 2019/04/14 23:03:57 Found no layout for "home", language "en", output format "HTML": create a template below /layouts with one of these filenames: index.en.html.html, home.en.html.html, list.en.html.html, index.html.html, home.html.html, list.html.html, index.en.html, home.en.html, list.en.html, index.html, home.html, list.html, _default/index.en.html.html, _default/home.en.html.html, _default/list.en.html.html, _default/index.html.html, _default/home.html.html, _default/list.html.html, _default/index.en.html, _default/home.en.html, _default/list.en.html, _default/index.html, _default/home.html, _default/list.html
INFO 2019/04/14 23:03:57 Found no layout for "404", language "en", output format "HTML": create a template below /layouts with one of these filenames: 404.html

                   | EN
+------------------+----+
  Pages            |  3
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0

Total in 10 ms
Watching for changes in /Users/mxu/Projects/Writing/hugo-tuflove-theme/exampleSite/{content,data,layouts,static}
Watching for config changes in /Users/mxu/Projects/Writing/hugo-tuflove-theme/exampleSite/config.toml
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

Connet to the listed URL (http://localhost:1313/). You might see a blank page sicnce there's no HTML file in public/ folder. To veryfy the built-in web server, you can manually add "index.xml" or "sitemap.xml" to the URL. For example, http://localhost:1313/index.xml or http://localhost:1313/sitemap.xml should show content of these two xml files.


## Create a skeleton theme

## Create a static homepage

## Add content to the homepage

## Add content to the posts

## Creat a post listing

## Create top level pages


## Create the Header and Footer Partials

## Update the Home Page Template to Use the Partials

## Update the Default Single Template to Use the Partials

## Add “Date Published” to Posts and template

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments
* Hat tip to anyone whose code was used
