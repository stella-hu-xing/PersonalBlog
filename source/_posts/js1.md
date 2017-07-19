---
title: JavaScript Study Notes1
date: 2017-07-07 16:51:31
tags: JavaScript
---

### Using document.write() after an HTML document is fully loaded, will delete all existing HTML:
   The document.write() method should only be used for testing.

```
<!DOCTYPE html>
<html>
<body>

<h1>My First Web Page</h1>
<p>My first paragraph.</p>

<button onclick="document.write(5 + 6)">Try it</button>

</body>
</html>
```

### JavaScript Identifier

In JavaScript, the first character must be a letter, or an underscore (_), or a dollar sign ($).
Subsequent characters may be letters, digits, underscores, or dollar signs.

### Case sensitive

All JavaScript identifiers are case sensitive. 
The variables 'lastName' and 'lastname', are two different variables.

### Character set

JavaScript uses the Unicode character set.
Unicode covers (almost) all the characters, punctuations, and symbols in the world.

### The this Keyword

In JavaScript, the thing called this, is the object that "owns" the current code.
The value of this, when used in a function, is the object that "owns" the function.

Note that this is not a variable. It is a keyword. You cannot change the value of this.