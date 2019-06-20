# Hugo Tuflove Theme

Edward Tufte uses a distinctive style in his handouts: simple, with well-set typography, extensive sidenotes, and tight integration of graphics and charts. This project brings Tufte style to Hugo with responsive navigation bars.

This project is directly inspired by and based on

* [Tufte CSS](https://github.com/edwardtufte/tufte-css) - The Tufte style sheet for HTML documents
* [W3.CSS](https://www.w3schools.com/w3css/) - A CSS framework with simple and beautiful navigation bars
* [Hugo](https://gohugo.io/) - The content management framework used
* [Creating a new theme](https://github.com/digitalcraftsman/hugo-steam-theme/blob/master/exampleSite/content/post/creating-a-new-theme.md)

## Why you need a theme for writing
Wrting is a process of formulating coherent ideas. A good content management system decouples the writing process into two parts: content generation, and formating. This separation allows you to focus on content quality.

Format matters because contents need to be coded, in HTML for example, in order to be readible. 

Publishing your writings on the web is a great way to share ideas. In order to let people and yourself to read effectively, you need to publish in HTML format, which can be interpreted and presented by web browsers. So ideally you will be able to write in plain text or markdown and leave the HTML generation task to a content management system.

Content management system does two things, formating and indexing. 

There are hundreds of 

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


## Create a new theme
Hugo doesn't come with a default theme. We are going the create a new theme called tuflove (Tufte theme for Hugo lovers).

### Create a skeleton
```
$ hugo new theme tuflov
Creating theme at /Users/mxu/Projects/Writing/hugo-tuflove-theme/exampleSite/themes/tuflov

$ find themes -type f | xargs ls -l
-rw-r--r--  1 mxu  staff  1081 May 29 23:09 themes/tuflov/LICENSE
-rw-r--r--  1 mxu  staff     8 May 29 23:09 themes/tuflov/archetypes/default.md
-rw-r--r--  1 mxu  staff     0 May 29 23:09 themes/tuflov/layouts/404.html
-rw-r--r--  1 mxu  staff   250 May 29 23:09 themes/tuflov/layouts/_default/baseof.html
-rw-r--r--  1 mxu  staff     0 May 29 23:09 themes/tuflov/layouts/_default/list.html
-rw-r--r--  1 mxu  staff     0 May 29 23:09 themes/tuflov/layouts/_default/single.html
-rw-r--r--  1 mxu  staff     0 May 29 23:09 themes/tuflov/layouts/index.html
-rw-r--r--  1 mxu  staff     0 May 29 23:09 themes/tuflov/layouts/partials/footer.html
-rw-r--r--  1 mxu  staff     0 May 29 23:09 themes/tuflov/layouts/partials/head.html
-rw-r--r--  1 mxu  staff     0 May 29 23:09 themes/tuflov/layouts/partials/header.html
-rw-r--r--  1 mxu  staff   432 May 29 23:09 themes/tuflov/theme.toml
```

This skeleton includes templates (files ending in.html), license file, a description of your theme (theme.toml), and an empty archetype. Filling out he themoe.toml and LISENCE.md is optional. But it would be nice to declare them if you would like to distribute your theme.

Note that templete files at this skeleton stage are still empty. But we will change that and make them beautiful shortly.

### Update the Configure file to use the theme
Now that we have a theme to test with. It is a good idea to add the theme name to the configuration file. An alter native way is to add "-t tuflov" to explicitely specify theme in command line. 

```
$ vi config.toml

theme = "tuflov"
baseURL = ""
languageCode = "en-us"
title = "tuflov - Tufte for Hugo lovers"
```

### Gererate the site with the skeleton theme
Now let's generatethe site again with the empty theme
```
$ hugo --verbose
INFO 2019/05/29 23:17:03 No translation bundle found for default language "en"
INFO 2019/05/29 23:17:03 Translation func for language en not found, use default.
INFO 2019/05/29 23:17:03 i18n not initialized; if you need string translations, check that you have a bundle in /i18n that matches the site language or the default language.
INFO 2019/05/29 23:17:03 Using config file: /Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/config.toml
Building sites … INFO 2019/05/29 23:17:03 syncing static files to /Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/public/

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

Total in 25 ms
```

### Content vs. static
Hugo does two things when generating the site. It uses templates to transform content into HTML and it copies static files into the site. Unlike content, static files are not transformed. They are copied exactly as they are.

Hugo assumes that your site will use both CSS and JavaScript, so it creates directories in your theme to hold them. Remember opinions? Well, Hugo's opinion is that you'll store your CSS in a directory named css/ and your JavaScript in a directory named js/. If you don't like that, you can change the directory names in your theme directory or even delete them completely. Hugo's nice enough to offer its opinion, then behave nicely if you disagree.
```
$ find themes/tuflov -type d | xargs ls -ld
drwxr-xr-x  7 mxu  staff  224 May 29 23:14 themes/tuflov
drwxr-xr-x  3 mxu  staff   96 May 29 23:14 themes/tuflov/archetypes
drwxr-xr-x  6 mxu  staff  192 May 29 23:14 themes/tuflov/layouts
drwxr-xr-x  5 mxu  staff  160 May 29 23:14 themes/tuflov/layouts/_default
drwxr-xr-x  5 mxu  staff  160 May 29 23:14 themes/tuflov/layouts/partials
drwxr-xr-x  4 mxu  staff  128 May 29 23:14 themes/tuflov/static
drwxr-xr-x  2 mxu  staff   64 May 29 23:14 themes/tuflov/static/css
drwxr-xr-x  2 mxu  staff   64 May 29 23:14 themes/tuflov/static/js
```

## Theme development cycle
When you're developing a theme, you will make changes (in the theme dir), rebuild the site, and check your chages (in the browser).
1. Purge he the Public/ directory.
2. Run the build in web server in watch mode.
3. review your site in a browser.
4. Update theme.
5. Return to step 3.

## Theme development commands
Use the following commands as the basis of your workflow
```
# purger old public, static files
$ rm -rf public

# run hugo in watch mode
$ hugo server --watch --verbose

```

## Create a static homepage
Right now, there is no homepage yet. Hogo server will look for one of three files inthe the them's layout/ directory
1. index.html
2. \_default/list.html
3. \_default/single.html

We could update one tof the default template, but a good design decision is to update the *most specific* template available. That is not a hard and fast rule, but it is a good generalization.

Right now, that page is empty because we don;t have an content or any logic in the template. Let's change that by adding some text to the template.
```
$ vi themes/tuflov/layouts/index.html
<!DOCTYPE html> 
<html> 
<body> 
  <p>hugo says hello!</p> 
</body> 
</html> 
:wq

$
```
Build the web site and you'll be able to see a index.html being created under the public/ directory. Note that if you are running the server with the --watch option, the file may not be created. But you'll be able to see the change in a browser.

## Add content to the posts
Creating a static home page is a successful start point. Now let's create some content to the site. We'll display posts as a list on the home page and on their own page, too.

Hugo has a command to generate a skeleton post, just like it does for sites and themes.
```
$ hugo --verbose new post/first.md

INFO 2019/06/06 20:09:08 No translation bundle found for default language "en"
INFO 2019/06/06 20:09:08 Translation func for language en not found, use default.
INFO 2019/06/06 20:09:08 i18n not initialized; if you need string translations, check that you have a bundle in /i18n that matches the site language or the default language.
INFO 2019/06/06 20:09:08 Using config file: /Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/config.toml
INFO 2019/06/06 20:09:08 attempting to create "post/first.md" of "post" of ext ".md"
/Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/content/post/first.md created
```

```
cat  /Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/content/post/first.md

---
title: "First"
date: 2019-06-06T20:09:08-07:00
draft: true
---
```

Hogo uses an archetype to create the post file. We can create an archetype file specifically for the post type
```
$ vi themes/tuflov/archetypes/post.md

---
Description: ""
Tags: []
Categories: []
draft: true
---
:wq

$ find themes/tuflov/archetypes/ -type f | xargs ls -l
-rw-r--r--  1 mxu  staff   8 May 29 23:14 themes/tuflov/archetypes//default.md
-rw-r--r--  1 mxu  staff  60 Jun  6 20:31 themes/tuflov/archetypes//post.md


$ hugo --verbose new post/second.md
INFO 2019/06/06 20:32:58 No translation bundle found for default language "en"
INFO 2019/06/06 20:32:58 Translation func for language en not found, use default.
INFO 2019/06/06 20:32:58 i18n not initialized; if you need string translations, check that you have a bundle in /i18n that matches the site language or the default language.
INFO 2019/06/06 20:32:58 Using config file: /Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/config.toml
INFO 2019/06/06 20:32:58 attempting to create "post/second.md" of "post" of ext ".md"
/Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/content/post/second.md created


$ ls -l content/post/
total 16
-rw-r--r--  1 mxu  staff  68 Jun  6 20:09 first.md
-rw-r--r--  1 mxu  staff  60 Jun  6 20:32 second.md


$ cat content/post/first.md
---
title: "First"
date: 2019-06-06T20:09:08-07:00
draft: true
---

```

Hugo uses the section and type to find the template file for every content file. Hugo will first look for a template ile that matches the section or type name. If it can't find one, then it will look in the \_default/ directory. For now we can assume that Hugo will try posts/single.html, them \_defult/single.html
```
$ find themes/tuflov/ -name single.html | xargs ls -l
-rw-r--r--  1 mxu  staff  0 May 29 23:14 themes/tuflov//layouts/_default/single.html
```

We could create a new template, /posts/single.html, or change the default. 

Let's start with updating the default. It is good to start here because we can stat to build the basic layout for the site. As we add more content types we'll frfactor this file and move logic around. 

### update the tempalte file
```
$ vi themes/tuflov//layouts/_default/single.html
<!DOCTYPE html>
<html>
<head>
  <title>{{ .Title }}</title>
</head>
<body>
  <h1>{{ .Title }}</h1>
  {{ .Content }}
</body>
</html>
:wq
```

Build the web site and verify the results.
```
$ rm -rf public
$ hugo --verbose

INFO 2019/06/06 23:35:19 No translation bundle found for default language "en"
INFO 2019/06/06 23:35:19 Translation func for language en not found, use default.
INFO 2019/06/06 23:35:19 i18n not initialized; if you need string translations, check that you have a bundle in /i18n that matches the site language or the default language.
INFO 2019/06/06 23:35:19 Using config file: /Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/config.toml
Building sites … INFO 2019/06/06 23:35:19 syncing static files to /Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/public/
INFO 2019/06/06 23:35:19 found taxonomies: map[string]string{"tag":"tags", "category":"categories"}

                   | EN
+------------------+----+
  Pages            |  7
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0

Total in 13 ms


$ find public -type f -name '*.html' | xargs ls -l
-rw-r--r--  1 mxu  staff  126 Jun  6 23:35 public/index.html
-rw-r--r--  1 mxu  staff  104 Jun  6 23:35 public/posts/first/index.html
-rw-r--r--  1 mxu  staff  106 Jun  6 23:35 public/posts/second/index.html
```
Notice that the posts now have content. You can go to localhost:1313/posts/first/ to verify.




## Add content to the homepage
The home page will contain a list of posts. Let's update its template to add the posts that we just created.
```
$ vi themes/tuflov/layouts/index.html

<!DOCTYPE html>
<html>
<body>
  <p>hugo says hello!</p>
  {{ range first 10 .Data.Pages }}
    <h1>{{ .Title }}</h1>
  {{ end }}
</body>
</html>
:wq
```

Hugo uses the Go template engine. That engine scans the template files for commands which ar enclosed between "{{" and "}}". In this template ,the commands are:
1. range
2. .Title
3. end
The "range" command is an iterator. We use it to loop through the first ten pages. Every HTML file that ugo createds is trated as a page, so looping through the list of pages will look at every file that will be created.

The ".Title" command print the value to the "title" variable. Hugo pulls it from the front matter in the Markdown file.

The "end" command signals the ened of the range iterator. The engine loops back to the top of the iteration when it finds "end"

Build the web site and then veryfy the resutls.
```
$ rm -rf public
$ hugo --verbose

INFO 2019/06/06 23:23:39 No translation bundle found for default language "en"
INFO 2019/06/06 23:23:39 Translation func for language en not found, use default.
INFO 2019/06/06 23:23:39 i18n not initialized; if you need string translations, check that you have a bundle in /i18n that matches the site language or the default language.
INFO 2019/06/06 23:23:39 Using config file: /Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/config.toml
Building sites … INFO 2019/06/06 23:23:39 syncing static files to /Users/mxu/Projects/Writing/hugo-tuflov-theme/exampleSite/public/
INFO 2019/06/06 23:23:39 found taxonomies: map[string]string{"tag":"tags", "category":"categories"}

                   | EN
+------------------+----+
  Pages            |  5
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0

Total in 4 ms


```
### Link list items to context
The posts are listed on the home page. Let's add a link from there to the post. Since this is the home page, we'll update its template.
```
$ vi themes/tuflov/layouts/index.html
<!DOCTYPE html> 
<html> 
<body> 
  <p>hugo says hello!</p>
  {{ range first 10 .Data.Pages }}
    <h1><a href="{{ .Permalink }}">{{ .Title }}</h1>
  {{ end }} 
</body> 
</html> 
:wq
```
Build the web site and verify the results.


## Creat a post listing
We have the posts displaying on individual pages and on the home page. It is also useful to create a list of all posts (not just the first ten).

Let's use the default list template as a starting point.
```
$ find themes/tuflov -name list.html | xargs ls -l
-rw-r--r--  1 mxu  staff  0 May 29 23:14 themes/tuflov/layouts/_default/list.html
```

Hugo content list documents can be found from [Here](https://gohugo.io/templates/lists/).
```
$ vi themes/tuflov/layouts/_default/list.html

{{ define "main" }}
<main>
    <article>
        <header>
            <h1>{{.Title}}</h1>
        </header>
        <!-- "{{.Content}}" pulls from the markdown content of the corresponding _index.md -->
        {{.Content}}
    </article>
    <ul>
    <!-- Ranges through content/posts/*.md -->
    {{ range .Pages }}
        <li>
            <a href="{{.Permalink}}">{{.Date.Format "2006-01-02"}} | {{.Title}}</a>
        </li>
    {{ end }}
    </ul>
</main>
{{ end }}
```
The above list template will output the following html:
```
public/posts/index.html
<!DOCTYPE html>
<html>
<body>
  <p>hugo says hello!</p>

    <h1><a href="/posts/second/">Second</h1>

    <h1><a href="/posts/first/">First</h1>

</body>
</html>
```

## Create top level pages
Let's create a 'About' page to display at the top level.
```
$ vi content/about.md 
---
title: "About"
description: "about this site"
date: 2019-06-15T16:00:33-07:00
draft: false
slug: "about"
---

## about us

i'm speechless
:wq
```
Rebuild the web site:
```
cat public/about-time/index.html
<!DOCTYPE html>
<html>
<head>
  <title>About</title>
</head>
<body>
  <h1>About</h1>


<h2 id="about-us">about us</h2>

<p>i&rsquo;m speechless</p>

</body>
</html>
```

Notice that the 'About' page was created under the directory defined by the 'slug' tage in about.md.

The 'About' page also being listed on the home page. This is undesired. 
```
cat public/index.html
<!DOCTYPE html>
<html>
<body>
  <p>This is the home page</p>

    <h1><a href="/about/">About</h1>

    <h1><a href="/posts/second/">Second</h1>

    <h1><a href="/posts/first/">First</h1>

</body>
</html>
```

Let's change that.
```
$ vi themes/tuflov/layouts/index.html

<!DOCTYPE html>
<html>
<body>
  <p>This is the home page</p>
  <h1>posts</h1>
  {{ range first 10 .Data.Pages }}
    {{ if eq .Type "post"}}
      <h2><a href="{{ .Permalink }}">{{ .Title }}</a></h2>
    {{ end }}
  {{ end }}

  <h1>pages</h1>
  {{ range .Data.Pages }}
    {{ if eq .Type "page" }}
      <h2><a href="{{ .Permalink }}">{{ .Title }}</a></h2>
    {{ end }}
  {{ end }}
</body>
</html>
:wq
```
Regenerage the web site. Now the home page has two sections, posts and pages. Each section has the right set of heading s and links in it.

## Create the Header and Footer Partials
A partial is a chunk of html code stored in a file so that it can be reused frequently. 
```
$ vi themes/tuflov/layouts/partials/header.html

<!DOCTYPE html>
<html>
<head>
        <title>{{ .Title }}</title>
</head>
<body>
:wq

vi themes/tuflov/layouts/partials/footer.html

</body>
</html>
:wq
```

## Update the Home Page Template to Use the Partials
The most noticeable difference between a template call and a partials call is the lack of path:
```
{{ template "theme/partials/header.html" . }}
```
versus
```
{{ partial "header.html" . }}
```
Both pass in the context. Let's chagen the home page template to use these new partials.

```
$ vi themes/tuflov/layouts/index.html

{{ partial "header.html" . }}
  <p>This is the home page</p>
  <h1>posts</h1>
  {{ range first 10 .Data.Pages }}
    {{ if eq .Type "posts"}}
      <h2><a href="{{ .Permalink }}">{{ .Title }}</a></h2>
    {{ end }}
  {{ end }}

  <h1>pages</h1>
  {{ range .Data.Pages }}
    {{ if eq .Type "page" }}
      <h2><a href="{{ .Permalink }}">{{ .Title }}</a></h2>
    {{ end }}
  {{ end }}


{{ partial "footer.html" . }}
```

## Update the Default Single Template to Use the Partials
```
$ vi themes/tuflov/layouts/_default/single.html

{{ partial "header.html" . }}

 <h1>{{ .Title }}</h1>
  {{ .Content }}

{{ partial "footer.html" . }}
```

## Add “Date Published” to Posts and template
Date is a common meta data being displayed on post pages. The front matter of our posts has a variable named "date". Let's display this value on post pages.
We'll start by updating the template used torender the posts. The emplate code will look like:
```
{{ .Date.Format "Mon, Jan 2, 2006" }}
```

Posts uses the default single template, so we'll change that file.
```
$ vi themes/tuflov/layouts/_default/single.html

{{ partial "header.html" . }}

 <h1>{{ .Title }}</h1>
 <h2> {{ .Date.Format "Mon, Jan 2, 2006" }} </h2>
  {{ .Content }}

{{ partial "footer.html" . }}

```

Generate the web site and verify the results. The posts now have the date displayed in them. However, the "about" page also has the date displayed.

There are a couple of ways to make the fate display only on postes. We could do a "if" statement like we did on the home page. Another way would be a to create a separate template for postes.

Let's create a new template type this time. This is called a section template.
```
$ mkdir themes/tuflov/layouts/posts
$ vi themes/tuflov/layouts/_default/single.html
{{ partial "header.html" . }}

  <h1>{{ .Title }}</h1>
  {{ .Content }}

{{ partial "footer.html" . }}
:wq
```

Now we'll update the posts' version of the single template. Hugo's template engine will buse this version over the default.
```
$ vi themes/tuflov/layouts/posts/single.html
{{ partial "header.html" . }}

  <h1>{{ .Title }}</h1>
  <h2>{{ .Date.Format "Mon, Jan 2, 2006" }}</h2>
  {{ .Content }}

{{ partial "footer.html" . }}
:wq
```
Note that we removed the date display from the default template and put it hin the post template. Generate the web site and verify the results. Postes have dates and the about page doesn't.


## Add CSS to the template



## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details


## Acknowledgments
* Hat tip to anyone whose code was used
