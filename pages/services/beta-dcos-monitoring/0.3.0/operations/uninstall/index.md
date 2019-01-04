---
layout: layout.pug
navigationTitle: Uninstall
title: Uninstall
menuWeight: 80
excerpt: Removing the Beta DC/OS Monitoring Service from a DC/OS cluster
render: mustache
model: /services/beta-dcos-monitoring/data.yml
---
#include /services/include/beta-software-warning.tmpl

# Uninstall the {{ model.techName }} service

You can uninstall the service using the following command:

```bash
dcos package uninstall {{ model.serviceName }}
```
