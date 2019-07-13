---
title: "Tips for creating flows"
keywords: tips
tags: [tips, help, workaround]
permalink: tips.html
summary: A useful guide speed up the process of making flows
---


Life is easier with these simple tips! For more information on how to use these nodes, check out the reference documentation.

## 1.  Don't wait for scheduled tasks

Create a "Test Button" by the side of scheduled tasks, so you can trigger them for test purposes. Leaving the button in at the end isn't a problem either! Definitely a timesaver rather than having to modify the task to 1 minute later every time you want to test!

{% include image.html file="tip_scheduledtask.png" alt="Scheduled flow" caption="Put a test button in parallel to the scheduled task" %}

## 2. Embed Documentation

Make sure the next person knows what you did! Put in an "Embedded Resource" node - but don't link it up to anything. Call the dataset "documentation" so everyone knows what it has in it.

{% include image.html file="tip_documentation.png" alt="Embedded resource as documentation" caption="Embed your documentation, and leave it unattached to your flow." %}

## 3. Think about load!

If you are sending 1000's of emails at 9am each day, consider using the "dripper" node to smooth out the peak load. Set it to drop emails in ever 1 second, so that you don't overload the email server!

{% include image.html file="tip_spikeload.png" alt="Dripper Node" caption="Use the dripper node to reduce load spikes" %}

## 4. Keep it simple: Use Markdown rather than HTML

Even if you are a coder, the next person may not be! Use the Markdown node so non-coders can make ammendments easily to their own emails! Keep complex code to a minimum where possible.

{% include image.html file="tip_nocode.png" alt="Markdown Node" caption="The markdown node can generate HTML from simple annotations" %}

## 5. If it really isn't working, consider side-loading breakpoints

Sometimes you want to inspect data, without stopping it. Try putting breakpoint nodes by the side of your flow, so you can collect data without stopping it. You can still release them, and when you do it still will not affect your flow.

{% include image.html file="tip_sidebreakpoint.png" alt="Lots of Breakpoints" caption="Put the breakpoints to one side in order to stop them stopping your flow" %}

