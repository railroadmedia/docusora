docusora
========

Documentation Methodology for Musora Media Inc.

* [Guidelines](#guidelines)
* [Tools, Online](#tools--online)
* [On Markdown Usage](#on-markdown-usage)
  + [Title](#title)
  + [Headers](#headers)
  + [Tables](#tables)
  + [RE Table of Contents](#re-table-of-contents)
  + [Syntax highlighting](#syntax-highlighting)

<!-- ecotrust-canada.github.io/markdown-toc -->


Guidelines
----------

* Write simply, but not so much that necessary detail is lost.
* Write in Markdown<sup>1</sup>
* Create Tables in CSV, generate markdown table from that, save CSV version in html comment block

<sup>1</sup> [CommonMark](http://commonmark.org/) to be exact, but don't worry too much about that. Different flavours of markdown are pretty hard to distinguish and generally play nice with each other (including [Github Flavored Markdown (GFM)](https://github.github.com/gfm/)).


Tools, Online
-------------

* editors (copy-paste for easy preview)
    * [very nice](https://jbt.github.io/markdown-editor/) 
    * [nice, but simple](http://markdown.pioul.fr)
    * [integrates with Google Drive](https://stackedit.io/)
* [CSV To Markdown Table Generator
](https://donatstudios.com/CsvToMarkdownTable)
    * select "*Use first line as header*"
    * select "*Comma Separated*"
* [generate empty tables structures](https://www.tablesgenerator.com/markdown_tables)
* [Table of Contents (TOC) Generator](https://ecotrust-canada.github.io/markdown-toc/)


On Markdown Usage
-----------------

### Title

Markdown doesn't have a way to make a document title. Generally people use the **h1** for that because it creates a document looks like we'd expect. There's two minor issues with this, but they don't concern us here, so we'll just use an **h1** to create the document title.

### Headers

Use 'em. See how to use markdown if you're unsure.

| header type |  if at start of same line |  if on line below            | 
|-------------|---------------------------|------------------------------| 
| h1          |  `#`                      |  `===` (continue as desired) | 
| h2          |  `##`                     |  `---` (continue as desired) | 
| h3          |  `###`                    |  *n/a*                       | 
| h4          |  `####`                   |  *n/a*                       | 
| h5          |  `#####`                  |  *n/a*                       | 
| h6          |  `######`                 |  *n/a*                       | 

<!--
header type, if at start of same line, if on line below
h1, `#`, `===` (continue as desired)
h2, `##`, `---` (continue as desired)
h3, `###`, *n/a*
h4, `####`, *n/a*
h5, `#####`, *n/a*
h6, `######`, *n/a*
-->

For example

```markdown
Header 1
====================

foo content


Header 2
---------------------

bar content


## Also Header 2

baz content


### Header 3

and so on and so forth...
```

Please put a space below each header for reliable rendering, and two spaces above

### Tables

Create Tables in CSV, generate markdown table from that, save CSV version in html comment block.

If change(s) required to Markdown table, please **do not edit it directly, but rather edit the CSV accordingly and re-generate the markdown table using the CSV-to-Markdown tool** noted elsewhere. This will ensure the CSV is always available for easy updates and will not become obsolete, leading to leg-work for future developers of creating CSV from Markdown table.

For example:

```markdown
| some column |  some other column |  an id maybe? |  sure why not | 
|-------------|--------------------|---------------|---------------| 
| foo         |  bar               |  1            |  true         | 
|             |  baz               |  2            |  false        | 
| qux         |  quxx              |               |               | 
|             |                    |               |  quuz         | 
| corge       |  grault            |  2839         |  maybe        | 


<!-- 
some column, some other column, an id maybe?, sure why not
foo, bar, 1, true
 , baz, 2, false
qux, quxx, , 
 ,  ,  , quuz
corge, grault, 2839, maybe
-->
```

Feel free to do whatever you want to make your CSVs easier to work with. Below is the exact same as above, just make a little easier to read by adding some spacing:

```
<!--
some column, some other column, an id maybe?, sure why not
foo,    bar,    1,      true
    ,   baz,    2,      false
qux,    quxx,    ,      
 ,       ,       ,      quuz
corge, grault,  2839,   maybe
-->
```

### RE Table of Contents

**Please update the TOC before committing.**

Copy your entire markdown file (`ctrl a` + `ctrl +c`) and paste into to the above noted online tool.

You will get something that looks like this:

```markdown
- [docusora](#docusora)
  * [Guidelines](#guidelines)
  * [Tools, Online](#tools--online)
  * [Details](#details)
    + [Tables](#tables)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>
```

There are two ways this can be improved before committing.

1. You don't need to include that link (just a link in an html comment to the tool will be sufficient).
2. you can remove the h1 item and move everything over to lines left. Because if we're using an h1 as a document title then there'll only be one - thus it's not necessary or helpful to have it in the TOC.

Much better:
 
```markdown
* [Guidelines](#guidelines)
* [Tools, Online](#tools--online)
* [Details](#details)
  + [Tables](#tables)

<!-- ecotrust-canada.github.io/markdown-toc -->
```

### Syntax highlighting

Where possible, please use this for your code blocks.

Example:

	```
	function(){
	    $foo = 'bar';
	}
	```

produces: 

```
function(){
    $foo = 'bar';
}
```

whereas

	```php
	function(){
	    $foo = 'bar';
	}
	```
  
produces:

```php
function(){
    $foo = 'bar';
}
```


