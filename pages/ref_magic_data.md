---
title: "Reference Manual: Magic Data"
keywords: reference
tags: [reference, magic, data]
permalink: ref_magic_data.html
summary: Functions related to getting data from XML.
---


## data(*dataset*, *xpath*)

The data function gets a bit of data from a dataset using XPath to find the specific bit of data in the document. These tags can be automatically generated through the Breakpoint Inspector

## markdowntable(*dataset*, *xpath*)

This tag automatically makes a table in markdown. It finds every instance of the xpath in a document, and then makes a table from it.

A typical XPath example is

```
/NewDataSet/Table
```

Because there are multiple rows output from a SQL query, the XPath will match each row (there are lots of table tags inside of the NewDataSet next to each other) and create a markdown table.
