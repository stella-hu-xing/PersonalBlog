---
title: markdown-note
date: 2017-06-20 16:47:09
tags: MarkDown

---

# Introduction of Markdown
Markdown is a lightweight and easy-to-use syntax for styling all forms of writing on the GitHub platform. It’s written in what nerds like to call “plaintext”, which is exactly the sort of text you’re used to writing and seeing.

# Syntax guide
#### Headers
``` bash
# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag
```
#### Emphasis
*This text will be italic*
_This will also be italic_
**This text will be bold**
__This will also be bold__
_You **can** combine them_
``` 
*This text will be italic*
_This will also be italic_
**This text will be bold**
__This will also be bold__
_You **can** combine them_
```
#### Lists
##### Unordered
* Item 1
* Item 2
  * Item 2a
  * Item 2b
```
* Item 1
* Item 2
  * Item 2a
  * Item 2b     
```
##### Ordered
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b
```
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b
```
#### Images
```
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
```
#### Links
http://github.com
[GitHub](http://github.com)
```
http://github.com - automatic!
[GitHub](http://github.com)
```
#### Blockquotes

As Kanye West said:
> We're living the future so
> the present is our past.
```
> We're living the future so
> the present is our past.
```
#### Inline code
I think you should use an `<addr>` element here instead.

#### Task Lists
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
```
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
```
#### Tables

You can create tables by assembling a list of words and dividing them with hyphens - (for the first row), and then separating each column with a pipe |:

First Header | Second Header| Third Header
------------ | -------------|------------
Content from cell 1 | Content from cell 2| Content from cell 3
Content in the first column | Content in the second column | Content in the third column
```
First Header | Second Header| Third Header
------------ | -------------|------------
Content from cell 1 | Content from cell 2| Content from cell 3
Content in the first column | Content in the second column | Content in the third column
```
(different from basic syntax, the second row dont have | at beginning and end)
