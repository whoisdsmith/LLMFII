---
aliases:
  - MarkdownToSiteGenerator
tags:
  - markdown
  - static-site-generator
  - dotnet
  - "#static-site-generator"
  - "#markdown"
  - "#content-parsing"
  - "#documentation"

  - "#csharp"
  - "#dotnet"
  - "#bootstrap"
---
# Markdown-To-Site Generator



![Build And Test](https://github.com/LeeReid1/MarkdownToSiteGenerator/actions/workflows/dotnet.yml/badge.svg)



This solution builds a static multiple-HTML-page site from a directory of markdown files that can be hosted without an application layer. The builder produces pages based on a standard Bootstrap HTML5 style, including a drop-down menu to navigate. Images, JS, and style sheets are placed in separate directories.



This solution is largely public as example of my personal code and development style. It is written from scratch in a test-driven-development oriented style, in C# 11 and .NET Core 7.0. 



The solution is designed to be extensible - parsing documents other than markdown, for example, or producing documents other than HTML. 



## How to Use



Build to solution in Visual Studio 17.4.2 or with the .NET Core command line tools. This will provide and executable. You can also build the unit tests.



Call the executable without arguments to see help documentation. Typically, you would simply call it like so:



```

MarkDownToSiteGenerator C:\my\directory\with\markdown_files\ C:\my\html\output\directory\

```



## Examples



You can see an example website in the Example_Input and Example_Output folders.



## Input Directory Structure



Directories can be nested as deep as you would like and will reflect the final site structure. Spaces in paths are converted to hyphens in the HTML site. The output directory must not be within the input directory, and vice versa.



### Settings



You can optionally include a config.ini file in the top directory of your input to change how the site is generated. See the examples folder for relevant settings.



## Links





### Linking between pages



To link between pages, link to the title of that file, not its path or destination

```

[the content of the link](title_of_the_that_file)

```



If your page title contains spaces, replace them with underscores in the link. For more information on titles, see Metadata in this document.



Links written in this way are checked for correctness. An exception is thrown if the page is not found.



The html sitemap can be linked to with the reserved title `sitemap` so long as the site map generation is turned on in config.



### Linking to URLs



You can also link directly to urls, which will not be altered, in the normal way. These must begin with `http://`, `https://` or `www.`:



```

[the content of the link](https://example.com)

```





### Home in the Navigation Bar



The navigation bar will link to your home page if you include the following in your config.ini file:



```

site_name=<the name of the link text you would like in the navigation bar>

home_page=<title of your home page> (not the path)

```



See Metadata in this document to understand the title. If you do not provide the `home_page` but do provide the `site_name` the link will be to `/`.





## Metadata



Add metadata to MD documents like so (including the blank line):

```

title: My page

author: Mike Dent



```



These, if any, must appear at the start of the document. All except `title:` will be placed in the HTML head as meta tags. Stick to letters (a-Z) for the keys.



### Title Tag



The title metadata tag is special and used for:



1. Building link text to that page

1. Linking internally to that page (see Linking Between Pages)

1. Setting `<title>` in the html head



If you do not provide a title tag, the first H1 is used in its place.



It's ok to use spaces in page titles. Take note that to link to pages which has spaces in the name, you should replace the spaces with underscores (see Linking Between Pages).



Don't use existing filenames such as my-image.jpg or `sitemap` as a title.



#### Avoid Duplicates

It is critical that your pages never have identical titles as it makes linking impossible. Duplicate titles will result in an exception.



Page titles are not case-sensitive. They are also considered duplicates if matching when spaces are replaced with underscores. For example:



```

my title == my_title

MyTiTlE == mytitle

My_TiTlE == my_title

```



## Style



Bootstrap is automatically included, unless turned off in the config file. Additional CSS files should be placed in the root directory. Any that are found are linked to in all generated html files.



## Limitations



* This is not intended to be a complete solution for all use cases and only covers a subset of Markdown syntax. It is readily extensible, though.

* Solution does not support old MacOS line endings (`\r`)