---
title: "Schedule Email Model"
keywords: models
tags: [model, example, introduction]
permalink: model_schedule_email.html
summary: Making a scheduled email is easy!
---

## Introduction

The following guide goes through the "today you have to..." or "things you forgot from yesterday" email. The template can be followed for most purposes.

## Logical Steps

The following blocks will allow you to build a scheduled email

### 1. [Scheduled Task] Schedule the email to run at a time

Bring a scheduled task block in, and a test button. Put them in parallel, so you can test your flow

### 2. [SQL Query] Get the list of potential recipients

Create a SQL statement listing your recipients. Group them, so you have one record per email address you will be sending to. Name this dataset "recipients"

Something like this is good

```SQL
SELECT vrt__ref, email___, naam____ FROM verte___ WHERE vrt__ref IN (SELECT vrt__ref FROM v1bon___ WHERE tst__ref='0500')
```

*In this example we get all the RFQs waiting to be quoted, and group them by their representitive. This means that there is one line for each representitive who needs to get an email.*

### 3. [XML Loop] Loop through the recipients

You now need to make a set of different jobs, each of which will generate a separate email for each recipient (assuming they are all personalised!)

Use the XML Loop function

- Loop Dataset will be "recipients"
- Loop XPath will be /NewDataSet/Table
- Repeater Dataset will be "contact"

If you had 10 recipients, you will now have 10 jobs, each one will run separately. Put a breakpoint in if you need some extra assistance in understanding what this does.

### 4. [SQL Query] Create the table for the email

Most emails need a table of data in them. The easiest way to do this is to create a SQL query, naming all the columns as you wish to have the in the email right now!

Call the dataset "email_table"

```SQL
SELECT kla__rpn AS CustomerKeyword, omschr__ AS EstimateDescription, leverdat AS DesiredDate FROM v1bon___ WHERE vrt__ref='<#dataset="contact" xpath="/Table/vrt__ref">' AND tst__ref='0500'
 ```

 *The contact dataset is unique for each job (or representative). This query makes a table of all the estimates that representive needs to follow up on.*

### 5. [Embedded Resource] Create a plain text email

Remember to use the markdown node to make emails easier to make. Use the markdowntable() function to turn your SQL query quickly into an HTML email table later on.

Call the dataset "email_text"

```
Your RFQ To Follow Up
=====================

Good morning! Below is a list of RFQ to follow up.

<%markdowntable("email_table", "NewDataSet/Table")%>

```

### 6. [Markdown] Make the HTML email with the Markdown block

To turn your text into HTML, use the markdown block.

In the "input" use the following expression:

```
<%data("email_text")%>
```

Call the dataset "email_html"

### 7. [Simple Email] Create and send the email

Template: Unbranded.html

Email Recipient

```
<%data("contact", "/Table/email___")%>
```

Email Subject:

```
RFQ to Follow Up
```

HTML Content:

```
<%data("email_html")%>
```

Text Content:

```
<%data("email_text")%>
```

## 8. Test

1. Set your email to dry run, and to the C:\Temp folder, so you can see what the email will look like
2. When you are happy, set "Dry Run" to "No" - and away you go!