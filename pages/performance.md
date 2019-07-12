---
title: "Measuring Performance"
keywords: performance
tags: [slow, wait, speed, CPU, disk]
permalink: performance.html
summary: Measuring the performance of a flow
---

## How do we measure performance?

Performance is measured, and monitored in "number of nodes processed per second". This is represented over different time periods and can be found in the statistics panel, in the CERM Flows editor.

{% include image.html file="performance_statspanel.png" alt="Statistics panel" caption="An example of a statistics panel in the CERM flows editor" %}

The screenshot above shows:

1. Over the last 1 minute, 0.27 nodes started and completed every second
2. Over the last 10 minutes 0.25 nodes were started and completed each second
3. Over the last 60 minutes 0.25 nodes started and 0.23 nodes completed

### Why is the number of started and completed nodes different?

If the number of started and completed nodes is different it normally means one of two things:
- There is a build-up of jobs in a node which is completing slowly
- There is a node which is producing errors, and therefore not completing jobs

You should take a look at the logs to rectify this problem
