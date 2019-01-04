---
layout: layout.pug
navigationTitle: Overview
title: Overview
menuWeight: 20
excerpt: Overview of Beta DC/OS Monitoring Service
render: mustache
model: /services/beta-dcos-monitoring/data.yml
---
#include /services/include/beta-software-warning.tmpl

{{ model.techName }} makes it easy to monitor services on your DC/OS cluster. The {{ model.techName }} service can be configured to automatically load Alert Manager configurations from a Git repository. The {{ model.techName }} service ships with a set of default Grafana dashboards for DC/OS, which you can configure directly. You can configure the Grafana UI from {{ model.techName }}. You can also set placement constraints to customize where a service is deployed.