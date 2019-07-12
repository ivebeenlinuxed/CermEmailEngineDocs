---
title: "Using Datasets"
keywords: data
tags: [data, dataset, job, inspect]
permalink: using_data.html
summary: Make dataset by collecting data from your inputs in order to make decisions and take action.
---

## What is a dataset?

At every stage of your flow you will generate data. For a timer - how often does it go off? For a button - who pressed it? All the answers to these questions can be answered using datasets.

Flow nodes can create datasets. Each node normally creates one dataset. The dataset can be named, and this is added to the job, alongside all the previous data that has been collected.

## Example Flow with Dataset

{% include image.html file="using_datasets_example.png" alt="Example Flow" caption="A flow with a timer and a simple email" %}

Both the email and the timer nodes have a property named "Dataset". This allows you to say what you want to call the data, so you can find it later. We may call the data "timer_data", and "email_data". We can then use these names later to identify where the data came from.

Considering a slightly different example, where a flow has two email nodes, you may want to call one "email_to_customer" and the other "email_to_representative".

The timer_dataset will now hold when the timer was triggered (the date and time), and how often it gets triggered. The email_data contains information about whether the email was sent, at what time it was sent and any information about how the server handled the email.

## Inspecting the Data

To view data in a dataset we can use the "breakpoint" node. The previous example contained a "breakpoint node" at the end of the flow. The dataset property of the Timer node was filled out with "timer_dataset", and the email node "email_dataset".

If we now start our flow, select the breakpoint node, wait for a job to arrive in the node properties and click inspect we can now see the data in the job.

Click a dataset on the left hand side to see it's contents

{% include image.html file="using_datasets_inspect.png" alt="Inspect Dataset" caption="Two datasets collected by a flow job" %}
