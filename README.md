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
* [Documentation Guidelines](#documentation-guidelines)
  + [Installation, Configuration, and General](#installation--configuration--and-general)
  + [Classes](#classes)
  + [Methods](#methods)
    - [notes](#notes)
    - [method use example](#method-use-example)
    - [method parameters](#method-parameters)
  + [method return value](#method-return-value)
* [API Reference Guidelines](#api-reference-guidelines)

<!-- ecotrust-canada.github.io/markdown-toc -->


Guidelines
----------

* documentation for an app or package should live in that repository's "README.md" file. 
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


Documentation Guidelines
------------------------

### Installation, Configuration, and General

As required:

1. describe installation instructions, including .env variables and/or configuration.
1. Create sections to describe any not easily-discoverable features, logic of features, "gotcha"s or things to watch out for. Ideally you just refactor such things out, but sometimes it's not worth it or just might not happen. Give future developers a fighting chance by giving them a heads-up so they don't go down rabbit-holes chasing tricky bugs.

### Classes

For package functionality accessed by injected classes, give each class it's own section. The header is the class's name.

Where applicable note the following:

1. If class is to be extended, or is an interface or abstract class, note this at the top of the classes' section.
1. If all methods to be noted below are public, note this at the top of the *class's* section.

### Methods

In each class's section, create a sub-section for each method available for use by an implementation (*public* and *protected* methods). The sub-section's header is the method name.

Each method should have these three items:

1. notes
1. method use example
1. method parameters
1. method return value

#### notes

Describe in a sentence or two what the method does.

If it *might* be helpful, then *definitely* provide a paragraph or two with some illuminating background and explaination of what the method exactly does. Things like "behind-the-scenes" operations, why it was created, and what's generally happening in around the use of this method. Basically help give some context to future developers who may be refering to these docs but are not as aware of everything everything happening with this package and the kinds of systems it might be used for. 

Where applicable note the following:

1. If all methods in the class are public, state that at the top of the class's section.
1. If method is protected rather than public, state that at the top of that method's section.


#### method use example

Code samples make for easy comprehension, reminders, and copypasta programming.


#### method parameters

Use the following table to describe the parameters for each method:

| # |  name |  required |  default\* |  type |  description | 
|---|-------|-----------|------------|-------|--------------| 
|   |       |           |            |       |              | 

<!--
#, name, required, default\*, type, description
 ,  ,  ,  ,  ,
-->

Example:

| # |  name |  required |  default\* |  type    |  description                    | 
|---|-------|-----------|------------|----------|---------------------------------| 
| 1 |  foo  |  yes      |            |  string  |  name to save file as on remote | 
| 2 |  bar  |  yes      |            |  string  |  path to file to upload         | 
| 3 |  qux  |           |  true      |  boolean |  something descriptive          | 
 
<!--
#, name, required, default\*, type, description
1, foo, yes , , string, name to save file as on remote
2, bar, yes , , string, path to file to upload
3, qux, , true , boolean, something descriptive
-->

\* when applicable

Easy copypasta CSV template:

```markdown
<!-- replace *this line* with markdown table generated using donatstudios.com/CsvToMarkdownTable -->

<!--
#, name, required, default\*, type, description
 ,  ,  ,  ,  , 
 ,  ,  ,  ,  , 
-->

\* when applicable
```

If all params are required, remove the "default\*" column

| # |  name |  required |  type   |  description                    | 
|---|-------|-----------|---------|---------------------------------| 
| 1 |  foo  |  yes      |  string |  name to save file as on remote | 
| 2 |  bar  |  yes      |  string |  path to file to upload         | 
 
<!--
#, name, required, type, description
1, foo, yes , string, name to save file as on remote
2, bar, yes , string, path to file to upload
-->


### method return value

Detail each possibility in this table:

| result |  type |  data |  description | 
|--------|-------|-------|--------------| 
|        |       |       |              | 
  
<!--
result, type, data, description
 ,  ,
-->

example:

| result    |  type    |  data example                                        |  description                                             | 
|-----------|----------|------------------------------------------------------|----------------------------------------------------------| 
| succeeded |  string  |  {"foo":"bar"}                                       |  succeeded and returns value of "foo"                    | 
| failed    |  boolean |  {"failed":"reason failed is because of that thing"} |  failed and has json with explaination in "failed" value | 
 
<!--
result, type, data example, description
succeeded, string, {"foo":"bar"}, succeeded and returns value of "foo"
failed, boolean, {"failed":"reason failed is because of that thing"}, failed and has json with explaination in "failed" value
-->

Omit the "description" column if it's superfluous.

| result     |  type    |  data  | 
|------------|----------|--------| 
| succeeded  |  boolean |  true  | 
| failed     |  boolean |  false | 

<!--
result, type, data
succeeded , boolean, true
failed , boolean, false
-->



API Reference Guidelines
------------------------

Create sections to help logically organize endpoints and functionality. Within sections, each endpoint has it's own header. The title of that header should be as succinct an explanation as is possible of what the endpoint does.

For example, if you have a "comment-like" url that can take a request with either a PUT or a DELETE method, you have two endpoints. But it wouldn't make sense to lable that endpoint in the reference by it's url and method because that's not descriptive enough.j

* comment-like PUT
* comment-like DELETE

or 

* like
* unlike 

Or maybe not? That top one actually looks pretty good.