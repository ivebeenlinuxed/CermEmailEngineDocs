---
title: "Accessing CERM Flows"
keywords: access
tags: [access, web, location, link, share, start, stop, delete]
permalink: accessing.html
summary: Access the CERM Flows software
---

## Accessing CERM Flows

CERM Flows is a component for the CERM Engine, and runs on IIS Web Services. To access, open a web browser.

- From a CERM Engine RDP session: [http://localhost/flows]
- From a Client: [http://cerm-engine/flows]

## Understanding the interface

The following screenshot shows the CERM Flows Interface. Below is a legend to the highlighted functions.

### CERM Flows Index

{% include image.html file="accessing_index.png" alt="Index Page With Numbering" caption="Screenshot of Index Page" %}

1. Download Pre-Made Flow (created by a consultant) by clicking this button, then clicking "Install" on the flow which will carry out the required function

2. Click "Add Flow" to create a new custom flow, ready for you to begin building your own automated workflow

3. These are a list of the current flows which are installed on your system

4. This shows the current flow is "Stopped", which means that this particular workflow is not switched on

5. This button opens the flow for further editing or debugging, taking you into the designer window

6. This button deletes the flow. A confirmation will appear. This cannot be undone.

7. Consultants can click the "Share" button and, using a username and password, publish the flow into the "Gallery" (See #1), so that others can use the flow in their business.

### Cerm Flows Editor

The CERM Flows editor can be accessed by clicking the "Add Flow" or "Open" buttons on the index page described above.

{% include image.html file="accessing_editor.png" alt="Editor Page With Numbering" caption="Screenshot of Editor Interface" %}

1. This is the flowchart *canvas*. Your new flowchart blocks will be added here

2. This button exits the editor and returns you to the "Index" (above)

3. This button saves your flow. If your flow is started, it will be stopped, and then restarted

4. This button stops or starts your flow. If the button says "Start Flow", it is currently stopped. If it says "Stop Flow" it is currently running.

5. This is a *Module*. A module contains a set of flow nodes which are related. It may be possible to add more "module packs" to the CERM flows software, which will provide extra module groups.

6. This is a *Flow Node*. A flow node can be added to your canvas by clicking on it

7. This is the *Properties Panel*. When you click on the background of the "Canvas" it will show the general properties of the flow. When you click a node it will display the properties of that flow node.

8. This is the *Debug Panel*. This tab will have log messages about your current flow for the last 5 minutes. All logs are stored in the CERM database, so you can access them quickly.

9. This is the *Statistics Panel*. The tab will show you how many nodes have run over different periods of time. More details can be found on the statistics help topic.
