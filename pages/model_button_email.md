---
title: "Software Button Email"
keywords: button email
tags: [button, email, model]
permalink: model_button_email.html
summary: A quick guide to a push button email
---

The following example is for a "please approve your product now to prevent rescheduling". The customer required this on a push button, so they could trigger it as they needed. This could be used for any email where the customer wishes a human input to trigger.


TODO

## Logical Steps

### 1. [Custom Button] Add a custom button to the software

Decide which module to add the custom button to. The button will allow you to fill in a title, and depending on the module, will return some of the globals.

### 2. [Filter] Make sure a row is selected

Normally we only want to fire an email if a row is selected. To do this, we need to check the variables to make sure a value is not blank.

An example of a check could be:

```
<%data("schedule_btn", "/Objects/Object/Property[1]/Property[2]")%>
```

*In the scheduling module, this returns the plandv__ ID so you are able to send an email based on the row selected*

### 3. [SQL Query] Get the email address 

### 4. [Filter] Filter blank emails

### 5. [Embedded Resource] Make an email text

### 6. [Markdown] Convert to HTML

### 7. [Simple Email] Send the email
