docusora
========

Documentation Methodology for Musora Media Inc.

- [docusora](#docusora)
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
      - [Template](#template)
    + [Methods](#methods)
      - [notes](#notes)
      - [method use example](#method-use-example)
      - [method parameters](#method-parameters)
        * [Template (for Easy copypasta)](#template--for-easy-copypasta-)
        * [Example](#example)
      - [method return value](#method-return-value)
        * [Template (for Easy copypasta)](#template--for-easy-copypasta--1)
        * [Example](#example-1)
    + [Template](#template-1)
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

Put a space below each header for reliable rendering.

Because of Markdown's lack of a way to properly mark a title, we're using the h1s for the title. There will only ever be one h1 in a document, and the h2s will then act as the *defacto* first order of headers. Not perfect, but oh well.


### Tables

Create Tables in CSV, generate markdown table from that, paste markdown version, but keep CSV version for (stored in an html comment block) for easy changes and regeneration of markdown table.

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

You don't need to include that link (just the tool's URL - in an html comment - will be sufficient). Also, the h1 is unnecessary but just leave it - it's too much a pain to remove and then adjust the indentation every time.

Much better:
 
```markdown
- [docusora](#docusora)
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

For package functionality accessed by injected classes, give each class it's own section. The header is the class's name.

Where applicable note the following:

1. If class is to be extended, or is an interface or abstract class, note this at the top of the classes' section.
1. If all methods to be noted below are public, note this at the top of the *class's* section.


#### Template

    Installation, Configuration, Use
    --------------------------------
    
    ### Installation
    
    <!-- put your details here -->
    
    ### Configuration
    
    <!-- put your details here -->
    
    ### Use
    
    <!-- put your details here -->
    
    ### Classes


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

At the top of each method's section, note whether it's public or protected. Omit me if all methods noted are public - in such cases note that all methods described are public (as described above). Do not include private methods.


#### method use example

Code samples make for easy comprehension, reminders, and copypasta programming. Include at least one.


#### method parameters

Use the following table to describe the parameters for each method:

| # |  name |  required |  default |  type |  description | 
|---|-------|-----------|----------|-------|--------------| 
|   |       |           |          |       |              | 
 
<!--
#, name, required, default, type, description
 ,  ,  ,  ,  ,
-->

##### Template (for Easy copypasta)

```markdown
<!-- replace *this line* with markdown table generated using donatstudios.com/CsvToMarkdownTable -->

<!--
#, name, required, default, type, description
 ,  ,  ,  ,  , 
 ,  ,  ,  ,  , 
-->
```


##### Example

| # |  name |  required |  default |  type    |  description                    | 
|---|-------|-----------|----------|----------|---------------------------------| 
| 1 |  foo  |  yes      |          |  string  |  name to save file as on remote | 
| 2 |  bar  |  yes      |          |  string  |  path to file to upload         | 
| 3 |  qux  |           |  true    |  boolean |  something descriptive          | 
 
<!--
#, name, required, default, type, description
1, foo, yes , , string, name to save file as on remote
2, bar, yes , , string, path to file to upload
3, qux, , true , boolean, something descriptive
-->

If all params are required, remove the "default" column.

| # |  name |  required |  type   |  description                    | 
|---|-------|-----------|---------|---------------------------------| 
| 1 |  foo  |  yes      |  string |  name to save file as on remote | 
| 2 |  bar  |  yes      |  string |  path to file to upload         | 
 
<!--
#, name, required, type, description
1, foo, yes , string, name to save file as on remote
2, bar, yes , string, path to file to upload
-->



#### method return value

Detail each possibility in this table:

| outcome |  return data type |  return data value (example) |  notes about return data | 
|---------|-------------------|------------------------------|--------------------------| 
|         |                   |                              |                          | 
 
<!--
outcome, return data type, return data value (example), notes about return data
 ,  ,  , 
 ,  ,  , 
-->



##### Template (for Easy copypasta)

```markdown
<!-- replace *this line* with markdown table generated using donatstudios.com/CsvToMarkdownTable -->

<!--
outcome, return data type, return data value (example), notes about return data
 ,  ,  , 
-->
```


##### Example

| outcome   |  return data type |  return data value (example)                           |  notes about return data                   | 
|-----------|-------------------|--------------------------------------------------------|--------------------------------------------| 
| succeeded |  string           |  `{"foo":"bar"}`                                       |  json with a value assigned to key "foo"   | 
| failed    |  boolean          |  `{"failed":"reason failed is because of that thing"}` |  json with explaination in "failed" value | 
 
<!--
outcome, return data type, return data value (example), notes about return data
succeeded, string, `{"foo":"bar"}`, json with a value assigned to key "foo"
failed, boolean, `{"failed":"reason failed is because of that thing"}`, fjson with explaination in "failed" value
-->

If all return data values are boolean, omit the "* (example)*" from the column label.

Omit the "notes about return data" column if it's superfluous.

| outcome    |  return data type |  return data value | 
|------------|-------------------|--------------------| 
| succeeded  |  boolean          |  true              | 
| failed     |  boolean          |  false             | 

<!--
outcome, return data type, return data value
succeeded , boolean, true
failed , boolean, false
-->


### Template
    
    #### Usage Example

    ```php
    
    # replace *this line* with example of how to call method
    
    ```
    
    #### Parameters

    <!-- replace *this line* with markdown table generated using donatstudios.com/CsvToMarkdownTable -->
    
    <!--
    #, name, required, default, type, description
     ,  ,  ,  ,  , 
     ,  ,  ,  ,  , 
    -->
    
    #### Responses
    
    <!-- replace *this line* with markdown table generated using donatstudios.com/CsvToMarkdownTable -->
    
    <!--
    outcome, return data type, return data value (example), notes about return data
     ,  ,  , 
    -->

(assumes method name is h3. If not, adjust above h4s accordingly)



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

*\[UNDER CONSTRUCTION\]*

