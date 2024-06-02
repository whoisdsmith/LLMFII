---
tags:
  - "#software-development"
  - "#open-source"
  - "#developer-tools"

  - "#static-site-generator"
  - "#markdown"
  - "#dotnet"
---
# MarkTheRipper

![MarkTheRipper](Images/MarkTheRipper.100.png)

MarkTheRipper - Fantastic faster generates static site comes from simply Markdowns.

[![Project Status: WIP – Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip)

## NuGet

| Package  | NuGet                                                                                                                |
|:---------|:---------------------------------------------------------------------------------------------------------------------|
| MarkTheRipper | [![NuGet MarkTheRipper](https://img.shields.io/nuget/v/MarkTheRipper.svg?style=flat)](https://www.nuget.org/packages/MarkTheRipper) |
| MarkTheRipper.Core | [![NuGet MarkTheRipper.Core](https://img.shields.io/nuget/v/MarkTheRipper.Core.svg?style=flat)](https://www.nuget.org/packages/MarkTheRipper.Core) |
| MarkTheRipper.Engine | [![NuGet MarkTheRipper.Engine](https://img.shields.io/nuget/v/MarkTheRipper.Engine.svg?style=flat)](https://www.nuget.org/packages/MarkTheRipper.Engine) |

## CI

| main                                                                                                                                                                 | develop                                                                                                                                                                       |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [![MarkTheRipper CI build (main)](https://github.com/kekyo/MarkTheRipper/workflows/.NET/badge.svg?branch=main)](https://github.com/kekyo/MarkTheRipper/actions?query=branch%3Amain) | [![MarkTheRipper CI build (develop)](https://github.com/kekyo/MarkTheRipper/workflows/.NET/badge.svg?branch=develop)](https://github.com/kekyo/MarkTheRipper/actions?query=branch%3Adevelop) |

----

[![Japanese language](Images/Japanese.256.png)](https://github.com/kekyo/MarkTheRipper/blob/main/README_ja.md)

## What is this?

TODO: Eventually this document will be converted by MarkTheRipper itself.

MarkTheRipper is a very simple and fast static site generator
that allows you to write content in markdown.
The main intended use is for blog sites,
but we have eliminated the need for complex structures and tools anyway,
as if you were writing an article on GitHub Gist likely.

If you already have .NET 6.0 installation, you can install it simply:

```bash
dotnet tool install -g MarkTheRipper
```

Alternatively, [you can download a binary distribution](https://github.com/kekyo/MarkTheRipper/releases) that is compatible with .NET Framework 4.71 or higher.

* Important as of 0.4.0, installation with dotnet tooling has a problem where the incorrect version is installed [(being fixed.)](https://github.com/kekyo/MarkTheRipper/issues/27)

Then at first time, you will need to run:

```bash
$ mtr init mininum
```

Will generate a sample files under your current directory as follows
(Don't be afraid! It's only TWO FILES with a few lines of content
and almost no extra definitions!)

* `contents` directory: `index.md`,
  It is a content (post) file written by markdown.
* `layouts` directory: `page.html`,
  When the site is generated, the markdown is converted to HTML and inserted into this layout file.

That's it! Just to be sure, let's show you what's inside:

### contents/index.md

```markdown
---
title: Hello MarkTheRipper!
tags: foo,bar
---

This is sample post.

## H2

H2 body.

### H3

H3 body.
```

### layouts/page.html

```html
<!DOCTYPE html>
<html lang="{lang}">
<head>
    <meta charset="utf-8" />
    <meta name="keywords" content="{tags}" />
    <title>{title}</title>
</head>
<body>
    <header>
        <h1>{title}</h1>
        <p>Category:{foreach category.breadcrumbs} {item.name}{end}</p>
        <p>Tags:{foreach tags} {item.name}{end}</p>
        <p>
            {foreach (take (older self) 1)}<a href="{relative item.path}">Older</a>{end}
            {foreach (take (newer self) 1)}<a href="{relative item.path}">Newer</a>{end}
        </p>
    </header>
    <hr />
    <article>
        {contentBody}
    </article>
</body>
</html>
```

If you look at the content, you can probably guess what happens.
MarkTheRipper simply converts the keywords and body into HTML and inserts it into the layout.
Therefore when customizing a layout,
common HTML/CSS/JavaScript techniques can be applied as is,
and there are no restrictions.

(MarkTheRipper is written in .NET, but the user does not need to know about .NET)

Let's generate the site as is. Generating a site is very easy:

```bash
$ mtr
````

If your directory structure is the same as the sample, just run ``mtr`` to generate the site.
Site generation is multi-threaded and multi-asynchronous I/O driven,
so it is fast even with a large amount of content.
By default, the output is under the `docs` directory.
In this example, the `contents/index.md` file is converted and placed in the `docs/index.html` file.

You will then immediately see a preview in your default browser:

![minimum image](Images/minimum.png)

Site generation will delete all files in the `docs` directory and generate them again each time.
If you manage the entire directory with Git,
you can commit the site including the `docs` directory.
Then you can check the differences of the actual generated files.
You can also push it straight to `github.io` and easily publish your site!

There are no restrictions on the file names of markdown files or the subdirectories in which they are placed.
If there are files with the extension `.md` under the `contents` directory,
it does not matter what kind of subdirectories they are placed in,
under what kind of file names, or even if there are many of them.
All `.md` files will be converted to `.html` files, keeping the structure of the subdirectories.

Files with non `.md` extensions will simply be copied to the same location.
Additional files, such as pictures for example,
can be placed as you wish to manage them,
and you can write markdowns with relative paths to point to them.

### Daily operation

MarkTheRipper automatically recognizes all markdown files placed under the `contents` directory.
If you want to write an article,
you can simply create a markdown file in any directory you like and start writing it.

Is even this operation a hassle? Yes, of course we know.
So, there is an easier way to create and place markdown files so you can concentrate on writing articles.

```bash
$ mtr new
```

This will generate a template markdown file directly under the `contents` directory,
based on the current date naming, and automatically open the default markdown editor.
Categories will be discussed in more detail later,
but if you want to place articles in categories, you can use:

```bash
$ mtr new foo/bar/baz
```

Will place the article in the nested category "foo", "bar" and "baz" in the category.

----

## A more practical sample

The samples generated by `mtr init minimum` are too simple (minimum is not a bad thing!),
but in case you want to see some more customized examples,
Several samples are built in as standard.

Two more examples are built in:

```bash
$ mtr init sidebar
$ mtr init standard
$ mtr init rich
````

You can specify the sample `sidebar`, `standard` or `rich`.
The following features are available:

|Name|Description|
|:----|:----|
|`sidebar`|Added sidebar navigation on `minimum` sample by CSS flex. If you want to design the whole thing from scratch, it is convenient because it does not contain any extra definitions.|
|`standard`|Looks like GitHub's code block design (but does not have syntax highlighting). Uses [bootstrap.js 5.0](https://getbootstrap.jp/).|
|`rich`|Syntax highlighting by [prism.js](https://prismjs.com/). Uses bootstrap.js 5.0.|

![standard image](Images/standard.png)

![rich image](Images/rich.png)

No need to worry. These samples have also been implemented
with the utmost care to keep the layout code to a simplest.
They are easy to understand and even HTML beginners
can start customizing with these samples.

----

## Layout details

MarkTheRipper layouts are very simple, yet flexible and applicable enough for your needs.
The layouts provide all keyword substitutions by referencing a "Metadata dictionary".

Here is an example of a layout substitution.

----

### Keyword Substitution

The simplest example is a simple keyword substitution. Suppose you define the following layout:

```html
<title>{title}</title>
```

This will replace the keyword `title` in the metadata dictionary with the corresponding value.
The value of `title` is defined at the beginning of the corresponding markdown document:

```markdown
---
title: Hello MarkTheRipper!
---

(... Body ...)
```

If you have tried other site generators, you may know how to add these special "header lines" to your markdown to insert a title, date, tags and etc.
MarkTheRipper also follows this convention syntactically, but is more flexible.
For example, the following example produces exactly the same result:

```html
<title>{foobar}</title>
```

```markdown
---
foobar: Hello MarkTheRipper!
---

(... Body ...)
```

* Note: This header is called "FrontMatter" in other site generators and is written in YAML syntax.
  However, MarkTheRipper does not strictly use YAML,
  because uses a syntax that allows for greater flexibility in text.
  For example, `title` is not required to be enclosed in double quotes,
  and `tags` is correctly recognized without square brackets.
  For the record, MarkTheRipper does not use the term "FrontMatter."

Do you somehow see how you can make use of metadata dictionaries?
In other words, MarkTheRipper can treat any set of "key-value" pairs you write in the markdown header as a metadata dictionary,
and you can reflect any number of them on the layout.

Arbitrary keywords can be substituted anywhere on the layout,
allowing for example the following applications:

```html
<link rel="stylesheet" href="{stylesheet}.css">
```

```markdown
---
title: Hello MarkTheRipper!
stylesheet: darcula
---

(... Body ...)
````

Perhaps this feature alone will solve most of the problems.

----

### Special keywords and fallbacks

There are several special but potentially important keywords in this metadata dictionary.
They are listed below:

|Keyword|Note|
|:----|:----|
|`generated`|Date and time when the site was generated.|
|`layout`|The name of the layout to apply.|
|`lang`|Locale (`en-us`, `ja-jp`, etc.)|
|`date`|Date of the post.|
|`timezone`|Timezone of the environment in which the site was generated by MarkTheRipper, in IANA notation, or time.|
|`published`|Ignore this markdown by explicitly specifying `false`.|

* There are several other special keywords, which will be explained later.

These keywords can be overridden by writing them in the markdown header.
It may not make sense to override `generated`, but just know that MarkTheRipper does not treat metadata dictionary definitions specially.

You may be wondering what the default values of `lang`, `layout` and `timezone` are.
Metadata dictionaries can be placed in `metadata.json`,
which is the base definition for site generation.
(It does not have to be there. In fact, it is not present in the minimum samples.)
For example, the following definition:

```json
{
  "title": "(Draft)",
  "author": "Mark the Ripper",
  "layout": "page",
  "lang": "en-us",
  "timezone": "America/Los_Angeles"
}
```

This reveals something interesting. The value of the `title` keyword is "(Draft)".
For example, consider the following layout:

```html
<meta name="author" content="{author}" />
<title>{title}</title>
```

If you specify `title` in the markdown, that title will be inserted,
otherwise the title "(Draft)" will be inserted.
Similarly, if `author` is specified, the name of author will be inserted,
otherwise "Mark the Ripper" will be inserted.

If you are thinking of using this for a blog, you may not want to put your name in the header of the markdown,
since most of your posts will be written by yourself.
However, the title will of course be different for each post.
In such cases, you can use the "fallback" feature of the metadata dictionary.

And as for the `lang` and `layout` fallback:

* Only if `layout` is not found in the fallback, the layout name `page` is used.
* Only if `lang` is not found in the fallback, the system default language is applied.

The layout name may need some supplementation.
The layout name is used to identify the layout file from which the conversion is being made.
For example, if the layout name is `page`, the file `layouts/page.html` will be applied. If:

```markdown
---
title: Hello MarkTheRipper!
layout: fancy
---

(... Body ...)
```

then `layouts/fancy.html` will be used.

The `date` represents the date and time of the article and is treated like an ordinary keyword,
but if it is not defined in the markdown header,
the date and time of generation will be inserted into the markdown header automatically.

The `timezone` is referenced when dealing with dates and times such as `date` and is the basis for time zone correction.
If the system timezone setting of the environment in which you run MarkTheRipper is different
from the date and time you routinely embed in your articles,
you may want to include it in the `metadata.json` file.
If your system's time zone setting is different from the date and time you routinely embed articles,
you may want to include it in the `metadata.json` file.
(A typical environment for this would be when running on a cloud service such as GitHub Actions.)

You may feel that `lang` is simply one of the ordinary keywords.
This is explained in the next section.

----

### Recursive keyword search

You may want to pull results from the metadata dictionary again,
using the keywords as the result of the metadata dictionary pull.
For example, you might want to look up:

```markdown
---
title: Hello MarkTheRipper!
category: blog
---

(... Body ...)
```

A `category` keyword is like a category of articles.
Here, it is named `blog`, but if you refer to it by keyword as follows:

```html
<p>Category: {category}</p>
```

The HTML will look like `Category: blog`.
This may work fine in some cases, but you may want to replace it with a more polite statement.
So you can have the metadata dictionary search for the value again,
using `blog` as the keyword.
Use the `lookup` function keyword built-in MarkTheRipper:

```html
<p>Category: {lookup category}</p>
```

* The details of the function keywords are explained in later chapters.

If you do this and register the pair `blog` and `Private diary` in the metadata dictionary,
the HTML will show `Category: Private diary`.

Such keyword/value pairs can be referenced by writing them in `metadata.json` as shown in the previous section.
In addition, the metadata dictionary file is actually all JSON files matched by `metadata/*.json`.
Even if the files are separated,
they will all be read and their contents merged when MarkTheRipper starts.

For example, it would be easier to manage only article categories as separate files,
such as `metadata/category.json`.

----

### Enumeration and nesting

For classifications such as "category" and "tag",
you would want to have the user select them from a menu and be taken to that page.
For example, suppose there are 5 tags on the entire site.
You would automatically add these to the page's menu.
To allow the user to navigate to a page classified under a tag from the menu, we can use the enumerator.
As usual, let's start with a small example.

This is the layout included in minimum:

```html
<p>Tags:{foreach tags} '{item}'{end}</p>
```

* The `tags` keyword indicates a list of tags (see below)

This means that documents between `{foreach tags}` and `{end}` will be repeated as many times as the number of `tags`.
"Documents between" are, in this case: ` '{item}'`.
Note the inclusion of spaces.
Likewise, it can contain line breaks, HTML tags, or anything else in between.

Now suppose we convert the following markdown:

```markdown
---
title: Hello MarkTheRipper
tags: foo,bar,baz
---

(... Body ...)
````

Then the output will be `<p>Tags: 'foo' 'bar'</p>`.
The `foo,bar` in `tags` have been expanded and quoted in the output, each separated by space.

Again, documents between `{foreach tags}` and `{end}` are output repeatedly, so you can use the following:

```html
<ul>
  {foreach tags}
  <li>{item.index}/{item.count} {item}</li>
  {end}
</ul>
```

Result:

```html
<ul>
  <li>0/3 foo</li>
  <li>1/3 bar</li>
  <li>2/3 baz</li>
</ul>
```

The `{item}` inserted between the tags is a keyword that can refer to each repeated value.
Also, specifying `{item.index}` will give you a number starting from 0 and counting 1,2,3....
`{item.count}` is the number of repetitions.
In the above there are 3 tags, so this value is always 3.

In addition, you can nest different keywords.
For example, for each category and you can enumerate multiple tags.

In addition, multiple keywords can be nested.
The following example repeats the tag twice:

```html
<ul>
  {foreach tags}
  {foreach tags}
  <li>{item.index} {item}</li>
  {end}
  {end}
</ul>
```

Result:

```html
<ul>
  <li>0 foo</li>
  <li>1 bar</li>
  <li>0 foo</li>
  <li>1 bar</li>
</ul>
```

Note, by the way, that `item` in this case refers to a double nested inner `tags` iteration.
In some cases, you may want to use the value of the outer iteration.
In that situation, you can specify a "bound name" for the `foreach`:

```html
<ul>
  {foreach tags tag1}
  {foreach tags tag2}
  <li>{tag1.index}-{tag2.index} {tag1}/{tag2}</li>
  {end}
  {end}
</ul>
```

Result:

```html
<ul>
  <li>0-0 foo/foo</li>
  <li>0-1 foo/bar</li>
  <li>1-0 bar/foo</li>
  <li>1-1 bar/bar</li>
</ul>
```

If the bound name is omitted, `item` is used.
Now you have a grasp of how to use `foreach` for repetition.

----

### Aggregate tags

Once you understand how to use repetition, you are as good as done with tags and categories.
MarkTheRipper automatically aggregates all the tags and categorizations of your content.
Tags can be referenced by the following special keywords:

|Keywords|Note|
|:----|:----|
|`tagList`|Aggregate list of all tags.|
|`rootCategory`|A category that is the root. (It is no classification)|

First, let's make a list of tags:

```html
<ul>
  {foreach tagList}
  <li>{item}</li>
  {end}
</ul>
```

Result:

```html
<ul>
  <li>foo</li>
  <li>bar</li>
  <li>baz</li>
       :
</ul>
```

In the previous section we repeated the use of `tags` defined for the markdown file, here we use `tagList`.
The difference is that we are not dealing with a single markdown file, but with the aggregated tags of all markdown files processed by MarkTheRipper.

In other words, you can use `tagList` to add menu items and link lists by tags.
How do I add a link to each tag entry?
Tags alone do not tell us the set of contents associated with a tag,
but in fact tags can be enumerated using `foreach`:

```html
{foreach tagList tag}
<h1>{tag}</h1>
{foreach tag.entries entry}
<h2><a href="{relative entry.path}">{entry.title}</a></h2>
{end}
{end}
```

Note that we specify the bound name to make it easier to understand what we are trying to enumerate.

Enumerating the `entries` property gives access to information about
the corresponding markdown group.
Using the property `path`, you get the path to the file corresponding to the content,
and use `title` to get its title (the `title` described in the markdown's header).

* `path` yields the path to the converted HTML file, not the path to the markdown.

By the way, this path is relative to the output directory.
If you embed the path in HTML, it must be relative to the directory where the HTML file resides.
To do this calculation, use MarkTheRipper's built-in function keyword `relative`:

```html
<h2><a href="{relative entry.path}">{entry.title}</a></h2>
```

Using `relative` to calculate the path will work correctly
how the HTML output by MarkTheRipper is deployed on any server.
This will be safer than using the reference path for hard-coded URLs.

----

### Aggregate categories

Categories can be referenced by the following special keywords:

|keywords|content|
|:----|:----|
|`category`|a hierarchical list of categories. Describe in the header part of each markdown|
|`rootCategory`|The root (unclassified) category|

The critical difference between tags and categories is that tags are defined in parallel,
while categories are defined with hierarchy. For example:

````
(root) --+-- foo --+-- bar --+-- baz --+-- foobarbaz1.md
         |         |         |         +-- foobarbaz2.md
         |         |         |
         |         |         +-- foobar1.md
         |         |
         |         +--- foo1.md
         |         +--- foo2.md
         |         +--- foo3.md
         |
         +--- blog1.md
         +--- blog2.md
````

In the above example, `foobarbaz1.md` belongs to the category `foo/bar/baz`.
And `blog1.md` does not belong to any category,
it is supposed to belong to implicit hidden `(root)` category inside MarkTheRipper.
It is the `rootCategory` keyword.

For tags we defined it using the `tags` keyword, but for categories we use the keyword `category`.
The definition corresponding to `foobarbaz1.md` above is:

```markdown.
---
title: Hello MarkTheRipper
category: foo,bar,baz
---

(... Body ...)
```

Specifies the hierarchy as a list. Note that unlike tags, this list represents a hierarchy.
CMSs and site generators often refer to such hierarchies as "breadcrumb" lists.

By the way, MarkTheRipper can determine the category from the directory name by simply placing
the content in a categorized subdirectory,
without having to specify the category with the `category` keyword.
Therefore, to categorize content by category, you only need to place it in categorized subdirectories.

Now that we have grasped the basic structure of categories,
let's actually write the layout.
First, enumerate the root category:

```html
<h1>{rootCategory.name}</h1>
<ul>
  {foreach rootCategory.entries entry entry}
  <li>{entry.path}</li>
  {end}
</ul>
```

Result:

```html
<h1>(root)</h1>
<ul>
  <li>blog1.html</li>
  <li>blog2.html</li>
</ul>
```

Since `rootCategory` represents the root category, its property `name` is `(root)`.
If this name is not appropriate for display,
you can replace it using recursive keyword search expression,
or you can write it directly since it is root in this example.

Then, like the tags, you can pull the header information for each markdown
from each of the elements enumerated in the `entries`.

Here, `path` is used to output the path to the content, but you can use `title` to output the title.
If you use `relative item.path`, you can get the path relative to the current content,
which can be used as the URL of the link to realize the link.

To enumerate categories, use the `children` property:

```html
<h1>{rootCategory.name}</h1>
{foreach rootCategory.children child1}
<h2>{child1.name}</h2>
{foreach child1.children child2}
<h3>{child2.name}</h3>
{end}
{end}
```

If we nest the enumerations repeately, we can enumerate all deep category structures.
Unfortunately, it is not possible to dynamically enumerate the category structure,
i.e., automatic recursively enumerate even the descendant categories that exist.
This is by design because MarkTheRipper does not have the ability to define any functions and recursive functions.
(Such a request is probably only for outputting a site-wide structure list, as we did not see the need for such a request.)

At the end of the category operation is an example of outputting breadcrumb list.
It is very simple:

```html
<ul>
  {foreach category.breadcrumbs}
  <li>{item.name}</li>
  {end}
</ul>
```

The `breadcrumbs` property returns a value that allows you to enumerate the categories leading to the target category,
starting from the root.
(However, if the target category is root, the root category is included; otherwise, it is not included.)

The individual elements enumerated are the same as for the categories described so far.
In the above example, the `name` property outputs the name of the category.

----

## Replacing keywords in markdown

The keyword replacement described so far is for "Layout" files.
It feature applies equally to markdown files.
For example, the keyword replacement in:

```markdown
---
title: hoehoe
tags: foo,bar,baz
---

Title: {title}
```

If you write such a markdown, `{title}` will be keyword-substituted in the same way.
Of course, the function keyword calculations described so far are also possible.

Keyword substitution on markdown does not work for code blocks:

````markdown
---
title: hoehoe
tags: foo,bar,baz
---

Title: `{title}`

```
{title}
```
````

As shown above, `{...}` are not interpreted by MarkTheRipper and are output as is.

----

### Function keywords

Here is a list of built-in functions, including the functions that have appeared so far:

|function|content|
|:----|:----|
|`format`|Format arguments into strings. |
|`relative`|Convert argument paths to relative paths. |
|`lookup`|Draws a metadata dictionary based on the results given by the `argument`. |
|`older`|Enumerates articles older than the argument indicates. |
|`newer`|Enumerates articles newer than the argument indicates. |
|`take`|Limit the number of items that can be enumerated. |
|`add`|Add numeric arguments.|
|`sub`|Subtract numeric arguments.|
|`mul`|Multiply numeric arguments.|
|`div`|Divide numeric arguments.|
|`mod`|Get the remainder of numeric arguments.|
|`embed`|Generate embedded content using [oEmbed protocol](https://oembed.com/) and etc.|
|`card`|Generate card-shaped content using [OGP metadata](https://ogp.me/) and etc.|

#### format

Formatting an argument into a string has always been possible without using `format` without any particular problem.
Where this function is particularly useful is when dealing with dates and times.

First, we show how the formatting is determined.
When using the `date` or `generated` keyword in such HTML:

```html
<p>Date: {date}</p>
```

The date and time are output in the following format:

```markdown
---
date: 2022/1/23 12:34:56
lang: en-us
---

(... Body text ...)
```

```html
<p>Date: 1/2/2022 12:34:56 PM +09:00</p>
```

This format varies depending on the language indicated by `lang`.
If `ja-jp` instead of `en-us`, then:

```html
<p>Date: 2022/01/02 12:34:56 +09:00</p>
```

Follow the standard format of the language.
The value of the `timezone` keyword is referenced when formatting the string,
and the timezone-corrected date and time are output.

And if you want to fix the format, use the `format` function as follows:

```html
<p>Date: {format date 'yyyy-MM-dd HH.mm.ss'}</p>
```

```html
<p>Date: 2022-01-02 12.34.56</p>
```

The first argument of the `format` function is an expression indicating the value to be formatted,
and the second argument is a format string.
The format specification string is enclosed in single or double quotes.

As previously mentioned,
"MarkTheRipper is written in .NET, but the user does not need to know about .NET",
only this format string follows the conventions of .NET.

The exact format of the date/time format string is [see this document](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings).

In fact, any value, not just dates and times, can be formatted according to the format.
For example, the `index` in the enumeration is a number, but can be formatted as:

```html
<p>{format item.index 'D3'}</p>
```

The number can be set to fixed three digits.

```html
<p>007</p>
```

The various format strings are also detailed around the .NET documentation listed above.

#### relative

As already explained, the `relative` function calculates a path relative to the current article path.

```html
<p>{relative item.path}</p>
```

You can also pass a string as an argument to the function. For example:

```html
<link rel="stylesheet" href="{relative 'github.css'}">
```

This way, you can specify the correct relative path where the stylesheet resides.
The path specified in the argument is relative to the site's root directory, `docs`.
In the above example, the path is relative to `docs/github.css`.

Normally, in such a case, you would specify an absolute path.
However, if you use an absolute path, it will be invalid depending on the deployment environment of your site.
Using the `relative` function improves the portability of the generated content.

#### lookup

The `lookup` function searches the metadata dictionary again for keywords
with the same name as the value specified in the argument.
A typical use case is to look up the name of a tag or category in the metadata dictionary:

```html
<p>Tag: {lookup tag}</p>
```

With `{tag}`, the true name of the tag is output,
but with the `lookup` function The output is obtained from the metadata dictionary
with the same keyword value as the tag name.
Thus, if `metadata.json` contains:

```json
{
  "diary": "What happened today"
}
```

You can actually swap the strings that are output.
As we have seen, you can also directly specify a value for a function argument,
so even if you want to output a fixed string, you can use:

```html
<p>Tag: {lookup 'diary'}</p>
```

#### older, newer (Article navigation)

You can use `older` and `newer` function to enumerate articles.
For example, to enumerate articles newer than the current article, use the following expression:

```html
{foreach (newer self)}<p>{item.title}</p>{end}
```

where `self` represents the current article (the markdown article currently using this layout) and the individual elements enumerated by `foreach` represent newer articles.
Thus, you can create links by referencing properties and applying the `relative` function as follows:

``html
{foreach (newer self)}<p><a href="{relative item.path}">{item.title}</a></p>{end}
```

Note the position of the parentheses.
In the above, the parentheses are used to specify `self` as an argument to the `newer` function.
Without the parentheses,
you have specified `foreach` with `newer` and `self` as arguments,
which will not work correctly.

The enumerated articles are obtained in date order.
Therefore, MarkTheRipper recommends that blog like post which are date-oriented;
to group them into category such as `blog` and use this function to navigate within those category.

`older` and `newer` function arguments can be expressions that indicate any articles.
An enumerated value of the `entries` property is equivalent.

#### take (enumeration operation)

`take` limits the number of possible enumerations of values.
For example, `tag.entries` will enumerate all articles with that tag:

```html
{foreach tags tag}
<h2>{tag}</h2>
{foreach tag.entries}<p>{item.title}</p>{end}
{end}
```

However, you may want to limit this to a few pieces:

```html
{foreach tags tag}
<h2>{tag}</h2>
{foreach (take tag.entries 3)}<p>{item.title}</p>{end}
{end}
```

The `take` function takes two arguments:
The first is the enumeration target and the second is the number of enumerations to limit.
The above expression limits the number to a maximum of 3.

There is a neat little technique using this `take` function and `foreach`.
It is applied in combination with the `newer` function in the previous section:

``html
{foreach (take (newer self) 1)}<a href="{relative item.path}">Newer: {item.title}</a>{end}
```

Limiting the number of articles to be enumerated to one means that if there are zero articles,
they will not be enumerated at all.
In other words, if there are no articles to enumerate,
the `foreach` will not be output, and therefore will not be displayed.
This means that if there are no articles newer than the current article,
the link will not be displayed.

This expression is almost identical to the sample layout.

#### add, sub, mul, div, mod (Numerical calculation)

These are functions that perform numerical calculations.
At least one argument is required, and if there are three or more arguments,
the calculation is performed consecutively. For example:

```html
<p>1 + 2 + 3 = {add 1 2 3}</p>
```

Adds all the numbers in the argument.
For complex calculations, use parentheses:

```html
<p>(1 + 2) * 4 = {mul (add 1 2) 4}</p>
```

You can nest any number of parentheses.
Parentheses can be applied and formatted as desired using the `format` function:

```html
<p>1 + 3 = {format (add 1 3) 'D3'}</p>
```

Result:

```html
<p>1 + 3 = 004</p>
```

The argument does not have to be a number,
as long as the string can be regarded as a number:

```html
<p>1 + 2 + 3 = {add 1 '2' 3}</p>
```

It is acceptable to have numbers containing decimals in the arguments.
If so, it will be treated as a calculation with decimals
(called "Floating-point operation"):

```html
<p>1 + 2.1 + 3 = {add 1 2.1 3}</p>
```

Results containing decimals may not always turn out as intended.
It may be better to always use the `format` function to account for such possibilities.
For information on how to specify formats that include decimals, [see here](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-numeric-format-strings#fixed-point-format-specifier-f).

Here is a simple example of using the calculation.
In enumeration, `item.index` is a number and starting from 0.
On the other hand, `item.count` is a number that can be enumerated,
but it is not a general notation if you put it in a sequence:

``html
<p>index/count = {item.index}/{item.count}</p>
```

Result:

```html
<p>index/count = 0/3</p>
<p>index/count = 1/3</p>
<p>index/count = 2/3</p>
```

In such a case, you can use `add` function to get:

```html
<p>index/count = {add item.index 1}/{item.count}</p>
```

Would result in a number from 1 to `count`,
which is closer to a natural representation.

Result:

```html
<p>index/count = 1/3</p>
<p>index/count = 2/3</p>
<p>index/count = 3/3</p>
```

#### embed (Generates embedded content)

The `embed` (and `card`, described below) functions are special,
powerful functions that generate content by reference to external data,
rather than performing simple calculations.
It is a powerful function that generates content by referencing external data.

Have you ever wanted to embed a YouTube video on your blog?
Or perhaps you have wanted to display card-shaped content to external content,
rather than just a link.

The `embed` and `card` functions make such complex content embedding easy.
For example, you could write the following in your document:

```markdown
## Found a great video!

One day, when I can travel freely, I would like to visit...

{embed https://youtu.be/1La4QzGeaaQ}
```

Then you will see the following:

![embed-sample1-en](Images/embed-sample1-en.png)

This image is not just a thumbnail.
You can actually play the video on the page. Magic! Is it?
This is made possible by using the standard [oEmbed protocol](https://oembed.com/)
to this is achieved by automatically collecting content that should be embedded in HTML.

The argument to the `embed` function is simply the "permalink" of the content,
i.e., the URL that should be shared.
In addition to YouTube, many other well-known content sites support this function, so:

```markdown
## Today's hacking

{embed https://twitter.com/kozy_kekyo/status/1508078650499149827}
```

![embed-sample2-en](Images/embed-sample2-en.png)

Thus, other content, such as Twitter, can be easily embedded. To see which content sites are supported, please [directly refer to oEmbed's json metadata](https://oembed.com/providers.json). You will see that quite a few sites are already supported.

However, one of the most useful sites we know of Amazon,
to our surprise does not support oEmbed!
Therefore, MarkTheRipper specifically recognizes Amazon's product links so that they can be embedded as well:

```markdown
## Learning from Failure

{embed https://amzn.to/3USDXfp}
```

![embed-sample3-en](Images/embed-sample3-en.png)

* This link can be obtained by activating Amazon associates.
  Amazon associates can be activated by anyone with an Amazon account, but we won't go into details here.

Now, a little preparation is required to use this handy function.
Prepare a dedicated layout file `layouts/embed.html` to display this embedded content.
The contents are only as follows:

```html
<div style="max-width:800px;margin:10px;">
    {contentBody}
</div>
```

As in the previous layout explanations,
the `contentBody` will contain the actual oEmbed content to be embedded.
The outer `div` tag determines the area of this embedded content.
In the above, the body is 800px wide with some space around the perimeter.
You may want to adjust this to fit your site's design.

If you need a different layout for each content site,
you can apply a file name like `layouts/embed-YouTube.html` that specifies the name of the oEmbed provider.

By the way, the oEmbed protocol may not contain embedded content.
In such a case, the oEmbed metadata that could be obtained together is used to generate content similar to the `card` function introduced next.

#### card (Generate card-shaped content)

The `embed` function directly displays embedded content provided by the content provider.
The `card` function collects content metadata and displays it in a view provided by MarkTheRipper.

Metadata is collected in the following way:

* oEmbed: Using the accompanying metadata (including cases where embedded content was not provided by the `embed` function)
* OGP (Open Graph protocol): Scraping the target page and collecting the OGP metadata contained in the page.
* Amazon: Collect from Amazon associates page.

Usage is exactly the same as the `embed` function:

```markdown
## Found a great video!

One day, when I can travel freely, I would like to visit...

{card https://youtu.be/1La4QzGeaaQ}
```

Then you will see the following :

![card-sample1-en](Images/card-sample1-en.png)

Unlike the `embed` function, it displays the additional information as content and links in a card-shaped format.
Similarly:

```markdown
## Learning from Failure

{card https://amzn.to/3USDXfp}
```

![card-sample3-en](Images/card-sample3-en.png)

Various content can be displayed in card-shaped format.
You can use either the embedded format or the card-shaped format as you like.

Like the `embed` function, the `card` function also requires a dedicated layout file.
The layout file `layouts/card.html` can be adapted to your site based on the following template:

```html
<div style="max-width:640px;margin:10px;">
    <ul style="display:flex;padding:0;border:1px solid #e0e0e0;border-radius:5px;">
        <li style="min-width:180px;max-width:180px;padding:0;list-style:none;">
            <a href="{permaLink}" target="_blank" style="display:block;width:100%;height:auto;color:inherit;text-decoration:inherit;">
                <img style="margin:10px;width:100%;height:auto;" src="{imageUrl}" alt="{title}">
            </a>
        </li>
        <li style="flex-grow:1;margin:10px;list-style:none; ">
            <a href="{permaLink}" target="_blank" style="display:block;width:100%;height:auto;color:inherit;text-decoration:inherit;">
                <h5 style="font-weight:bold;">{title}</h5>
                <p>{author}</p>
                <p>{description}</p>
                <p><small class="text-muted">{siteName}</small></p>
            </a>
        </li>
    </ul>
</div>
```

This template is completely independent HTML.
If you wish to use it in conjunction with Bootstrap,
please refer to the files included in the sample layouts generated by `mtr init standard` or `mtr init rich`.

Even the `card` function can be customized to be site-specific by naming the file `layouts/card-YouTube.html`.

----

## Install develop branch package

```
$ dotnet tool install -g MarkTheRipper --nuget-source http://nuget.kekyo.online:59103/repository/nuget/index.json
```

----

## License

Apache-v2.

----

## History

* 0.4.0:
  * Can be paging navigation. #20
* 0.3.0:
  * Ready to use oEmbed. #18
* 0.2.0:
  * Keyword expansion can be applied to the markdown document itself. #3
* 0.1.0:
  * Automatically inserted date metadata into markdown file when lacked. #13
  * Function calls can be made. #2
  * Aggregated categories and tags from entire content markdowns. #14
  * Bracket characters are supported. #6
  * Can use the generator keyword. #5
  * Automatic category collection is possible. #1
