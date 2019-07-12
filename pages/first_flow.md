---
title: "Building your first flow"
keywords: tutorial
tags: [tutorial, flow, start, email]
permalink: first_flow.html
summary: In this tutorial we will create a flow which sends a button when an email is clicked.
---

## Scenario

In this tutorial we are going to add our first flow. When we click a button in the flow tool, we will make the flow "send an email". The email is going to be saved in the directory "C:\Temp" on the CERM Engine. We use the "Dry run" function of the simple email tool, so we can test the emails without having to send them live.

{% include note.html content="Make sure the directory C:\Temp has been created on your CERM Engine, so your emails have somewhere to go" %}

## Adding the blocks

1. Add a Test Button node from the Flow Infrastructure module
2. Add a Simple Email node from the Email module
3. Join these two nodes together, so that the test button will trigger the email (the output of the button is connected to the email)
4. Set the email properties as follows:
  - Template: Unbranded.html
  - Email Recipient: test@test.com
  - Email Subject: Test Subject
  - HTML Content: Hello World!
  - Text Content: Hello World!
  - Dry Run: Yes
  - Dry Run Output Directory: C:\Temp\
  - Email Status Dataset: [Leave Blank]
5. Click Publish to Save

## Running the flow
1. Select the Test Button node
2. Click "Trigger"
3. Open the C:\Temp directory on the CERM Engine to see the created email!
