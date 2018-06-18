docusora
========

Documentation Methodology for Musora Media Inc.

- [docusora](#docusora)
  * [Guidelines & Tools](#guidelines---tools)
  * [for an Application or Package](#for-an-application-or-package)
    + [Installation, Configuration, and General](#installation--configuration--and-general)
    + [Methods](#methods)
      - [method use example](#method-use-example)
      - [method parameters](#method-parameters)
      - [method return value](#method-return-value)
  * [for an HTTP-accessible Web-API](#for-an-http-accessible-web-api)
    + [Elements to detail for each endpoint](#elements-to-detail-for-each-endpoint)
    + [Request Example](#request-example)
    + [Request Parameters](#request-parameters)
    + [Response Examples](#response-examples)

<!-- ecotrust-canada.github.io/markdown-toc -->


Guidelines & Tools
------------------

* documentation for an app or package should live in that repository's "README.md" file. 
* Write simply, but not so much that necessary detail is lost.
* Write in Markdown<sup>1</sup>
* Create Tables in CSV, generate markdown table from that, save CSV version in html comment block
* "[_template_README.md](https://github.com/railroadmedia/docusora/blob/master/_template_README.md)" is great. Use it to help guide yourself.

<sup>1</sup> [CommonMark](http://commonmark.org/) to be exact, but don't worry too much about that. Different flavours of markdown are pretty hard to distinguish and generally play nice with each other (including [Github Flavored Markdown (GFM)](https://github.github.com/gfm/)).

* editors
    * [jbt.github.io/markdown-editor/](https://jbt.github.io/markdown-editor/) 
    * [markdown.pioul.fr](http://markdown.pioul.fr)
    * [stackedit.io/](https://stackedit.io/)
* [CSV To Markdown Table Generator](https://donatstudios.com/CsvToMarkdownTable)
    * select "*Use first line as header*"
    * select "*Comma Separated*"
* [generate empty tables structures](https://www.tablesgenerator.com/markdown_tables)
* [Table of Contents (TOC) Generator](https://ecotrust-canada.github.io/markdown-toc/)


for an Application or Package
----------------------------------------------------------

Documentation for installed and configurable component or system typically addressed to back-end developers

See ['RemoteStorage' README.md](https://github.com/railroadmedia/remotestorage) for implemented usage.

### Installation, Configuration, and General

1. installation instructions, including .env variables and/or configuration.
1. Create sections to describe any not easily-discoverable features, logic of features, "gotcha"s or things to watch out for.
1. If class is to be extended, or is an interface or abstract class, note this at the top of the classes' section.
1. If all methods to be noted below are public, note this at the top of the *class's* section.


### Methods

Each method should have:

1. notes
1. method use example
1. method parameters
1. method return value

#### method use example

```php
$exists = $this->remoteStorageService->exists('foo/bar.jpg');
```

```php
/** 
 * @param Request $request
 * @return JsonResponse
 */
public function uploadThumbnailIfDoesNotAlreadyExist(Request $request)
{
    $target = 'foo/' . $request->get('target');    
    if(!$this->remoteStorageService->exists('foo/')){
        $upload = $this->remoteStorageService->put($target, $request->file('file'));
        throw_if((!$upload), new JsonResponse('Upload product thumbnail failed', 400));
    }
    return new JsonResponse(['exists' => true]);
}
```

#### method parameters

| #  |  name             |  required |  type    |  description                        | 
|----|-------------------|-----------|----------|-------------------------------------| 
| 1  |  filenameRelative |  yes      |  string  |  path to file name from bucket root | 
 
<!--
#, name, required, type, description
1 , filenameRelative, yes, string , path to file name from bucket root
-->


#### method return value

| outcome        |  return data type |  return data value | 
|----------------|-------------------|--------------------| 
| exists         |  boolean          |  true              | 
| does not exist |  boolean          |  false             | 

<!--   
outcome, return data type, return data value
exists, boolean , true 
does not exist, boolean , false 
-->


for an HTTP-accessible Web-API
------------------------------------------------------------

Give each resource its own section. Give each endpoint of that resource its own subsection. 

Title the endpoint sections with a descriptive title that is has brief as possible. For example, rather than calling a section "`GET /users/{id}`", call it "Get User"

See ['Usora' README.md](https://github.com/railroadmedia/usora/blob/d5aad09f2e7ba396c690ab448ec975281e5ed170/README.md) for implemented usage.

### Elements to detail for each endpoint

1. HTTP request method and URL\*
1. Notes\*
1. Request Example
1. Request Parameters
1. Response Examples

For the table in the "Responses" section with details about each possible response, if a content example is too long or unwieldy for the table, then in the table just put a note in brackets saying that the example is below. Then put it below. Putting the examples in 

### Request Example

```js
var userId = 1;

$.ajax({
    url: 'https://www.musora.com' +
        '/usora/user/show/' . userId,
    type: 'get',
    dataType: 'json',
    success: function(response) {
        // handle success
    },
    error: function(response) {
        // handle error
    }
});
```

### Request Parameters


| path\|query\|body |  key                  |  required |  default        |  description\|notes | 
|-------------------|-----------------------|-----------|-----------------|---------------------| 
| query             |  `limit`              |           | `25`            |                     | 
| query             |  `page`               |           |  `1`            |                     | 
| query             |  `order_by_column`    |           |  `'created_at'` |                     | 
| query             |  `order_by_direction` |           |  `'desc'`       |                     | 

<!--
path\|query\|body, key, required, default, description\|notes
query, `limit`, ,`25`,
query, `page`,  , `1`, 
query, `order_by_column`,  , `'created_at'`,
query, `order_by_direction`,  , `'desc'`,
-->

### Response Examples


    ##### `200 OK`
    
    ```json
    {
       "status":"ok",
       "code":200,
       "results":{
          "id":217988,
          "content_id":202313,
          "key":"difficulty",
          "value":"1",
          "type":"integer",
          "position":1
       }
    }
    ```
    
    ##### `418 I'm a teapot`
    
    ```json
    {
       "status":"I'm a teapot",
       "code":418,
       "results":{
          "coffee":0,
          "coffee-eta": 0,
          "error":"Am teapot. Cannot make coffee",
          "position":1
       }
    }
    ```

------------------------------------------------------------------------------------------------------------------------

The end.
