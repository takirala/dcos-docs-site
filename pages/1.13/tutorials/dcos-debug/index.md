---
layout: layout.pug
navigationTitle: Troubleshooting application deployment
title: Troubleshooting application deployment
excerpt: Provides tips for troubleshooting application deployment issues in a DC/OS cluster
render: mustache
model: /data.yml
menuWeight: 55
---
#include /include/tutorial-disclaimer.tmpl
<!-- ii. Intro/Set Expectations for this Tutorial -->

This tutorial provides a basic introduction to methods you can use to debug application issues during and after their deployment on DC/OS. You should consider this information to be a starting point rather than a comprehensive resource for troubleshooting issues when deploying applications on DC/OS.

You should keep in mind that debugging deployment issues in a distributed environment is often a challenging task. While DC/OS provides several tools for debugging, you might find it difficult to select the appropriate tool to use for a particular situation. You should also keep in mind that failures are likely when working with distributed systems because there are many components that must be configured to precise specifications to function together. 

Because of the interdependencies and complexities of working with multiple components, the best way to prevent potential issues from arising is through careful planning and preparation before, during, and after the initial installation and configuration of the cluster. You can also prevent many application deployment issues by putting extra care into the general design of your application architecture.

For more information and guidelines about designing the application architecture, consider the following resources:

- [Design your applications for debuggability](https://schd.ws/hosted_files/mesosconeu17/a6/MesosCon%20EU%202017%20University%20Slides.pdf)
- [Follow best practices for deployments](https://mesosphere.com/blog/improving-your-deployments/)
- [Set up monitoring and alerts so you can resolve issues as early as possible](https://docs.mesosphere.com/1.10/cli/command-reference/dcos-node/dcos-node-diagnostics/)
