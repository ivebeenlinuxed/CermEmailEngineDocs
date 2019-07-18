---
title: "Reference Manual: Magic String"
keywords: reference
tags: [reference, magic, data]
permalink: ref_magic_string.html
summary: Magic functions related to manipulating strings.
---


## substring(*data*, *start*, *length*)

This function will take a string, and return only a portition of the original text. Negative index removes from the end (-1 means take one character off the end).

Input:
```
<%substring('Worldd', 0, 5)%>
```

Output:
```
World
```

Input:
```
<%substring('Worldd', 0, -1)%>
```

Output:
```
World
```
