---
aliases:
  - obsidian-custom-classes
tags:
  - "#software-development"
  - "#developer-tools"
  - "#open-source"

  - "#obsidian-plugin"
  - "#markdown-customization"
  - "#html-classes"
---
<h1 align="center">Obsidian Custom Classes</h1>

<div align="center">
	<img alt="GitHub Workflow Status" src="https://img.shields.io/github/actions/workflow/status/LilaRest/obsidian-custom-classes/semantic-release.yml">
	<img alt="GitHub Downloads" src="https://img.shields.io/github/downloads/LilaRest/obsidian-custom-classes/total?color=%23ddccee">
	<img alt="GitHub License" src="https://img.shields.io/github/license/LilaRest/obsidian-custom-classes?color=%235588ff">
	<img alt="Semantic-release: angular" src="https://img.shields.io/badge/semantic--release-angular-e10079?logo=semantic-release">
</div>

<br>

<p align="center"><b>A minimal Obsidian plugin that allows you to add your own HTML<br>classes to chosen Markdown blocks directly from your notes.</b></p>

<br>
<br>

## Usage
You can add custom classes to :
<ul>
<li><p><b>entire blocks</b> <samp>(e.g. a whole list)</samp> &rarr; By inserting <code><samp>`class: &lt;customClass&gt;`</samp></code> on the line right before it</p>
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

```markdown
`class: fancy-list`
- Lorem ipsum
- Dolor
- Amet consectetur             
```
</p></td>
<td><p>

```html
<div class="fancy-list">
  <ul>
    <li>Lorem ipsum</li>
    <li>Dolor sit</li>
    <li>Amet consectetur</li>            
  </ul>
</div>
```
</p></td>
</tbody>
</table>
	</li>
  <br>
<li><p><b>specific elements</b> <samp>(e.g. a list item)</samp> &rarr; By inserting <code><samp>`class: &lt;customClass&gt;`</samp></code> inside of it</p>
  
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

```markdown
- Lorem ipsum
- Dolor sit `class: fancy-item`
- Amet consectetur
```
</p></td>
<td><p>

```html
<div>
  <ul>
    <li>Lorem ipsum</li>
    <li class="fancy-item">Dolor sit</li>
    <li>Amet consectetur</li>
  </ul>
</div>
```
</p></td>
</tbody>
</table>
	</li>
  <br>
  </li>
<li><p><b>or even both :</b>
	
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

```markdown
`class: fancy-list`
- Lorem ipsum
- Dolor `class: fancy-item` sit 
- Amet consectetur
```
</p></td>
<td><p>

```html
<div class="fancy-list">
  <ul>
    <li>Lorem ipsum</li>
    <li class="fancy-item">Dolor sit</li>
    <li>Amet consectetur</li>
  </ul>
</div>
```
</p></td>
</tbody>
</table>
	</li>
</ul>

<br>

> #### ℹ️ &nbsp; For advanced usages and/or informations see the [FAQ section](#-FAQ).

<br>
<br>
<br>

## Demonstrations
Here are some ways to use this plugin that may inspire you for your workflows.

<ins><b>Add a class to :</b></ins>

<ol>
<li>
<details>
  <summary><b>A whole table</b></summary>
<br>
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

```markdown
`class: mytable`
| AAA | BBB | CCC |
| --- | --- | --- |
| 111 | 222 | 333 |
```
</p></td>
<td><p>

```html
<div class="mytable">
<table>
  <thead>
    <tr>
      <th>AAA</th>
      <th>BBB</th>
      <th>CCC</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>111</td>
      <td>222</td>
      <td>333</td>
    </tr>
  </tbody>
</table>
</div>  
```
</p></td>
</tbody>
</table>
  <br>
</details>
</li>

<li>
<details>
  <summary><b>A table cell</b></summary>
  <br>
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

```markdown
| AAA | BBB                  | CCC |
| --- | -------------------- | --- |
| 111 | 222 `class: my-cell` | 333 |
```
</p></td>
<td><p>

```html
<div>
<table>
  <thead>
    <tr>
      <th>AAA</th>
      <th>BBB</th>
      <th>CCC</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>111</td>
      <td class="my-cell">222</td>
      <td>333</td>
    </tr>
  </tbody>
</table>
</div>  
```
</p></td>
</tbody>
</table>
  <br>
</details>
</li>
<li>
<details>
  <summary><b>A Dataview query</b></summary>
<br>
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

````markdown
`class: my-dv-list`
```dataview
LIST
WHERE creation
```
````
</p></td>
<td><p>

```html
<div class="my-dv-list">
  <div class="block-language-dataview">
    <ul class="dataview list-view-ul">
      // The results of your query 
      // <li>...</li>
      // ...
    </ul>
  </div>
</div>
```
</p></td>
</tbody>
</table>
  <br>
</details>
</li>

<li>
<details>
  <summary><b>A heading</b></summary>
<br>
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

```markdown
`class: important-title`
### My super heading
```
</p></td>
<td><p>

```html
<div class="important-title">
  <h3>My super heading</h3>
</div>
```
</p></td>
</tbody>
</table>
  <br>
</details>
</li>

<li>
<details>
  <summary><b>A blockquote</b></summary>
<br>
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

```markdown
`class: interesting-quote`
> Lorem ipsum dolor sit amet
```
</p></td>
<td><p>

```html
<div class="interesting-quote">
  <blockquote>
    <p>Lorem ipsum dolor sit amet</p>
  </blockquote>
</div>
```
</p></td>
</tbody>
</table>
  <br>
</details>
</li>

<li>
<details>
  <summary><b>An inline formatting</b></summary>
<br>
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

```markdown
I'm a **bold text `class: big`** and _`.small` me an italic one_
```
</p></td>
<td><p>

```html
<p>I'm a <strong class="big">bold text</strong> and <em class="small">me an italic one</em></p>
```
</p></td>
</tbody>
</table>
  <br>
</details>
</li>
</ol>
  
<br>
<br>
<br>

## Showcase / Integrations
That section displays some example of how people have integrated the _Custom Classes_ plugin in their workflows.
Feel free to share yours by [opening an issue](https://github.com/LilaRest/obsidian-custom-classes/issues/new).

<ol>
	<li><h3>The Lila's frontmatter :cherry_blossom:</h3>
  
Here the _Custom Classes_ plugin is used to render a Markdown unordered list (`ul`) as a clean frontmatter block.

&rarr; Source: https://forum.obsidian.md/t/a-frontmatter-that-finally-supports-links-lilas-frontmatter/53087
	
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

```markdown
`class:meta`
- creation:: 2023-01-21T18:55:12
- author:: [[John Doe]]
- parents:: [[Note]], [[Another note]]
- status:: #MayBePartial
```
</p></td>
<td><p>

| Theme | |
| -- | -- |
| Dark | ![](https://forum.obsidian.md/uploads/default/original/3X/1/4/1418a3659b033fcf8d925105d6a3da3c6b9984fc.gif) |
| Light | ![](https://forum.obsidian.md/uploads/default/original/3X/3/5/35b209dfa79a2b3df13166e9ddd6d1b208480fca.gif) |

</p></td>
</tbody>
</table>
</li>
</ol>

<br>
<br>
<br>

## ❔ FAQ
<details>
  <summary><b>Why not to use <code>&lt;div class="my-custom-class"&gt;</code> instead ?</b></summary>
  <blockquote align="center">
  <br>
    
  In Obsidian, wrapping a Markdown element in a `div` will break its render in Live Preview and Read modes, and prevent links from being clicked in Edit mode. Also, writing HTML into your notes makes them less readable.
    
  **Thanks to the _Custom Classes_ plugin you're able to add a custom classes to Markdown elements without breaking anything and using plain-markdown format !** :tada:
  </blockquote>
  <br>
</details>

<details>
  <summary><b>Will it works in other Markdown editors ?</b></summary>
  <blockquote align="center">
  <br>
    
  Since this plugin is exclusive to Obsidian, the custom classes will not be applied in other editors.
    
  However since the custom classes blocks (``` `class: ...` ```) are simple Markdown inline code-blocks, they will properly render as code blocks in other Markdown editors.
  </blockquote>
  <br>
</details>

<details>
  <summary><b>Is it possible to add multiple classes at once ?</b></summary>
  <blockquote align="center">
  <br>
    
  Yes, just separate each class by a comma :
<table align="center">
<thead>
<td align="center"><b>This markdown</b><br/><samp>(Edit mode)</samp></td>
<td align="center"><b>Will be rendered</b><br/><samp>(Live Preview / Read mode)</samp></td>
</thead>
<tbody>
<td><p>

```markdown
`class: first, second, third-one`
I'm the paragraph and you ?          
```
</p></td>
<td><p>

```html
<div class="first second third-one">
  <p>I'm the paragraph and you ?</p>
</div>
```
</p></td>
</tbody>
</table>
  </blockquote>
  <br>
</details>

<details>
  <summary><b>Does it works in Live Preview mode ?</b></summary>
  <blockquote align="center">
  <br>
  
  Yes the Live Preview mode is fully supported by this plugin.
  
  By the way, elements targetted by a _Custom Classes_ block are rendered in the exact same way in both Read and LP modes, allowing you to write CSS that will work everywhere.
  </blockquote>
  <br>
</details>

<details>
  <summary><b>The <code>class:</code> prefix is too long, is there any shorthand version ?</b></summary>
  <blockquote align="center">
  <br>
  
  Yes the _Custom Classes_ plugin will also consider as custom classes block every inline code-block that starts with `cls:`or with `.`
  
  So ``` `cls: wow` ``` and ``` `.wow` ``` are equivalent to ``` `class: wow` ```.
  </blockquote>
  <br>
</details>

<br>
<br>
<br>

## Installation
1) Go to **Community Plugins** section of your Obsidian's settings
2) Click on **Browse** and search for "Custom classes"
3) Select the _Custom Classes_ plugin and click on **Install**
4) Once installed, click on **Enable**
5) Enjoy !


<br>
<br>
<br>

## Inspiration
This plugin is originally inspired by the [Obsidian Stylist](https://github.com/ixth/obsidian-stylist) plugin but has been entirely rewritten to :
- focus exclusively on adding custom HTML classes,
- support the Live Preview mode,
- fix some majors bugs (e.g. classes were not properly appended if the targetted block was modified and then re-rendered).

<br>
<br>
<br>

## Contributing
See [CONTRIBUTING.md](https://github.com/LilaRest/obsidian-custom-classes/blob/main/CONTRIBUTING.md).
