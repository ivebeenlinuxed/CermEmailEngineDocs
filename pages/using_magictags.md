---
title: "Using a Magic Tag"
keywords: magic tag
tags: [magic, tag, variable]
permalink: using_magictags.html
summary: Use the data you have collected to make decisions and fill out information in forms automatically.
---

## What is a magic tag

A magic tag allows you to fill out information automatically, using the dynamic data that you have collected in the datasets. It can create sentences to put in an email, or be used to make decisions.

Consider the following XML dataset called "timer_release":

```xml
<?xml version="1.0" encoding="utf-16"?>
<Timer>
  <ReleaseDateTime>2019-07-12T23:11:53.0679434+02:00</ReleaseDateTime>
  <ReleaseInterval>8</ReleaseInterval>
</Timer>
```

We could now create an expression to say "Hi, Your job was released at 2019-07-12T23:11:53.0679434+02:00" by using the following magic tag:

```
Hi, Your job was released at <%data("timer_dataset", "/Timer/ReleaseDateTime")%>
```

{% include note.html content="Try this example by pasting it into the breakpoint inspector!" %}

## How does this work?

All data in Cerm Flows is stored as XML. This makes it really easy to read. If you have any other form of data, we use data converts to convert it to XML if the Cerm Flows system needs to use it (For example CSV to XML).

A *magic tag* is a bit of code which is replaced by something the system can generate. Magic tags use "functions". The function here is called data(). In the first quotes we put in the name of the dataset, and in the second, the XPath which directs the computer to the specific bit of information you need.

All systems which use XML use XPath to pick out bits of data.

{% include note.html content="You will NEED to take this 5 page tutorial on XPath. <a href='https://www.w3schools.com/xml/xpath_intro.asp'>Click here to view this now</a>" %}

Other magic text functions can be found in the Magic Text Reference section of the help

## Making a decision based on data

In order to make a decision on data we need to write an expression. Here we're going to keep it easy and ask:
 - Was the timer set to release on an 8 second delay?

### Setup the scenario

{% include image.html file="using_magictag_simpleflow.png" alt="Simple flow example" caption="Create the flow as shown above" %}

1. Add a timer from the timers module, set it for 8 second intervals, and call the dataset "timer_dataset"

2. Add a filter from the flow infrastructure module. Click "Add Filter" link in the properties, and fill the following information

{% include image.html file="using_magictag_filterdemo.png" alt="Filter properties" caption="Set the filter to the settings above" %}

The magic tag looks like this
```
<%data("timer_dataset", "/Timer/ReleaseInterval")%>
```

3. Add two breakpoint nodes, as shown in the screenshot
4. Publish and start the flow

### Results

- When you click on the breakpoint from the "True" output, you can see that datasets are being added to it.
- When you click the breakpoint on the "false" output, you can see there are no datasets.

The system has now used a magic tag to make a decision on whether your timer was set to 8 seconds!

### An example with two different timer inputs

Now add another timer, this time set it to a number other than 8, for example, 10. You now have two timers, one triggering a job every 8 seconds, the other every 10 seconds.

Publish this flow and make sure it is started.

{% include image.html file="using_magictag_twotimerflow.png" alt="Two Timers" caption="Example with two timers" %}

When you inspect the two breakpoints, all the 10 second jobs have been separated from the 8 second jobs, each going to their own breakpoints. You have now filtered the jobs and can apply different logic for both!

### Real world examples

All real world flow applications contain a certain amount of filtering:
- Filter (or check) if the customer is over their credit limit, and set a status on the product not to start the artwork.
- If a customer is proforma, unapprove the sales orders until payment


