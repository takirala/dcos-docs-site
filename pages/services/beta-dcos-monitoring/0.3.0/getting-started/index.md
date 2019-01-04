---
layout: layout.pug
navigationTitle: Getting Started
title: Getting Started
menuWeight: 30
excerpt: Get up and running quickly with Beta DC/OS Monitoring service
render: mustache
model: /services/beta-dcos-monitoring/data.yml
---

#include /services/include/beta-software-warning.tmpl

In this section, you will download and install the {{ model.techShortName }} package. 

# Prerequisites

- DC/OS Enterprise 1.12 or later.
- [DC/OS CLI](/latest/cli/install/) is installed.
- You are logged in as a superuser.

## Install package registry

Please follow these [instructions](https://docs.mesosphere.com/1.12/administering-clusters/repo/package-registry/quickstart/) to install the package registry.

# Install {{ model.techName }} service

## Download the package

Download the `.dcos` package of the {{ model.techName }} Service from the [Mesosphere support site](https://support.mesosphere.com/s/downloads).

# Install the service

Install the service with the `dcos registry add` command.
Assume that the downloaded package is called `{{ model.packageName }}.dcos` in the current working directory.

```bash
dcos registry add --dcos-file {{ model.packageName }}.dcos
dcos package install {{ model.packageName }} --package-version=<VERSION>
```
Among other things, this will install the package CLI.

## Verify service deployment
After installing the package CLI, you can monitor the deployment of your service. Run the command:

```bash
dcos {{ model.packageName }} plan show deploy
```

