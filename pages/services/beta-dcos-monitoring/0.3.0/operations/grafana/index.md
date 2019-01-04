---
layout: layout.pug
navigationTitle: Grafana
title: Using Grafana with Beta DC/OS Monitoring service
menuWeight: 20
excerpt: Using Grafana with the Beta DC/OS Monitoring service
render: mustache
model: /services/beta-dcos-monitoring/data.yml
---
#include /services/include/beta-software-warning.tmpl

The {{ model.techName }} service ships with a set of default Grafana dashboards for DC/OS, which you can configure directly. You can configure the Grafana UI from {{ model.techName }}.