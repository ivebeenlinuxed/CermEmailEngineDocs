---
title: "Using the Editor"
keywords: access
tags: [editor, using, mouse, remove, add, keyboard, drag, node, edit]
permalink: using_editor.html
summary: This page will tell you how to use the editor, and the mouse and keyboard controls
---

## The scenario

In this trial we shall be creating a push button, which when pressed will trigger an email to be sent. We guide through the steps required to do this.

### Creating a new flow

1. Go to the Index (see [Accessing CERM Flows]), and click "Add Flow".

You will now have a blank editor ready to go

### Adding an item to the flowchart

1. Click the "Flow Infrastructure" module, then click "Test Button", This will add a new test button node to the canvas.
2. Drag the node which has now been added to your canvas, towards the center, in order to position it.
3. Click on the "Email" module, and click "Simple Email". A new simple email node will be added to the screen.
4. Drag this node to a suitable location to the right of the test button.

{% include image.html file="using_editor_addnode.png" alt="Two nodes on a canvas" caption="Your canvas should look like this" %}

Notes:
 - As you click a node it will become selected, and have a "blue" border. This shows you which node you are currently looking at
 - You can left click the title of any node to highlight or select it.

### Joining two nodes together

1. Click on the "Output" label of the "Test Button"
2. Click on the "Input" label of the "Simple Email".

The two nodes will now be connected.

{% include image.html file="using_editor_connectnode.png" alt="Two nodes on a canvas" caption="Your canvas should look like this" %}

Notes:
 - You can link the same output to the inputs of multiple different nodes, for example you may wish to send an email and update a status at exactly the same time.

### Accessing the properties of a node

To see the current properties of the Simple Email node:

1. Select it
2. Scroll down the left panel, to find the properties panel (your properties will be blank)

{% include image.html file="using_editor_properties.png" alt="Two nodes on a canvas" caption="You can fill in information here" %}

Note:
 - Make sure you click Publish to save your changes!

### Disconnecting two joined nodes

Right click on the joining line between two nodes to remove the connection

### Deleting a node

Right click the node. It will now be deleted.

### Undo an action

If you misclicked, refresh the page. If you have not published your flow, the changes will not have been saved.
