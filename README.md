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

## Generate HTML from Markdown for the new site

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
