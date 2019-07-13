---
title: "Real Time Notification Email Model"
keywords: models
tags: [model, real time, trigger, example, introduction]
permalink: model_realtime_email.html
summary: A quick guide to instant notifications
---


The following example is for an email which alerts the user when a new RFQ is added to the system to be calculated. This could however be used to notify an account manager that a proforma invoice has now been paid or similar.

## Logical Steps

### 1. [SQL Trigger] Create a Trigger

Add a trigger so that the flow is launched as soon as something happens on a particular database table

*In this example we are creating an "INSERT" trigger on "Estimates". We will call this dataset "estimate_insert"*

### 2. [Filter] Filter out data

Most of the time the trigger will pick out too much data. The next thing to do is to filter out those rows which are not required.

*Here we are picking out every estimate on our trigger. We will now filter out those which only have the status 0500 - which is a new RFQ. Connect the "true" filter to the next node.*

```
<%data("estimate_insert", "/SqlTrigger/Insert/inserted/@tst__ref")%>
```

```
=
```

```
0500
```

### 3. [SQL Query] Get the email address that we are going to send the notification to

We must now get the email address from the database, so we can send a notification. We can do this with a simple select statement, looking up the email based on the reference ID of the row that was changed or added in the database.

We will call this dataset "contact"

```
SELECT verte___.email___ FROM v1bon___ LEFT JOIN verte___ ON verte___.vrt__ref=v1bon___.vrt__ref WHERE bon__ref='<%data("estimate_insert", "/SqlTrigger/Insert/inserted/@bon__ref")%>'
```


### 4. [Filter] Filter out where the email address is blank

There are likely to be some times when the email address of the person you wish to send the notification out to is blank. In that case it is important to filter these out.

```
<%data("email", "/NewDataSet/Table[1]/email___")%>
```

```
!=
```

```
[Leave this Blank]
```

### 5. [Embedded Resource] Make a markdown email text

Use the embedded resource to make an email text to send.

Call this dataset "email_text"

```
New RFQ
======

A new RFQ (ID: <%data("estimate_insert", "/SqlTrigger/Insert/inserted/@bon__ref")%>) is awaiting calculation
```

### 6. [Markdown] Make your HTML email text

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
<%data("contact", "/NewDataSet/Table[1]/email___")%>
```

Email Subject:

```
New RFQ: <%data("estimate_insert", "/SqlTrigger/Insert/inserted/@bon__ref")%>
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