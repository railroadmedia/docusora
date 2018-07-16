# Code Style Standards

This guide is based off all the main PSR standards. Please review each below (emphasis on PSR-1 & PSR-2):

**Code style & rules:**  
<https://www.php-fig.org/psr/psr-1/>  
<https://www.php-fig.org/psr/psr-2/>

Auto loading:  
<https://www.php-fig.org/psr/psr-4/>

Logging interface:  
<https://www.php-fig.org/psr/psr-3/>

Caching interface:  
<https://www.php-fig.org/psr/psr-6/>

# Overview

The goal of this document is to ensure the same code style is maintained across all our repositories.
Developers should be able to jump between projects and easily recognize and read the code.

# The Guide

**Fully read through PSR2 standards. This guide will continue off this document: <https://www.php-fig.org/psr/psr-2/>**

Example Ideal Function Style:
![Example Ideal Function Style](https://i.imgur.com/aOnJUB4.png)

## Doc Blocks

- Functions MUST have a doc block
- The doc block SHOULD have a description, and it should be a in full sentences with periods
- The doc blocks description MUST be start on the second line of doc block
- There MUST be a empty line between a doc blocks descriptions and the parameter/return declarations
- In the doc block: parameter types, return types, and throwable types MUST be declared if necessary

## Lines

- Code lines MUST NOT be longer than 120 characters
- Code SHOULD be chopped down rather than wrapped to stay under 120 characters
![Wrapping Style](https://i.imgur.com/DIO1oSR.png)
 
## Return Statements

- Return lines SHOULD have a new line before them
- Return lines MUST NOT have a new line after them IF the following line is a closing brace }
![Return Lines](https://i.imgur.com/wzxqoze.png)

## Chained Functions

- If the total chain length is longer than 120 characters, each function MUST be on a new line (chopped down)
 ![Chained Functions](https://i.imgur.com/JD5Gusj.png)

# PHPStorm Setup

1. Download the phpstorm-settings/musora-php-code-style.xml file fro, this repository <https://raw.githubusercontent.com/railroadmedia/docusora/master/phpstorm-settings/musora-php-code-style.xml>
2. Import it in to PHPStorm by selecting the file from your computer:
![Import PHPStorm Code Style](https://i.imgur.com/Bey4jRA.png)

**You can now automatically style your code to these standards using the auto format shortcut (Ctrl + Alt + L) (or whatever you
have it set to).**