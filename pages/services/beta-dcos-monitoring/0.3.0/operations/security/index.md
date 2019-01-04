---
layout: layout.pug
navigationTitle: Security 
title: Integrating Beta DC/OS Monitoring Service with DC/OS access controls
menuWeight: 50
excerpt: Running Beta DC/OS Monitoring Service on DC/OS clusters securely
render: mustache
model: /services/beta-dcos-monitoring/data.yml
---
#include /services/include/beta-software-warning.tmpl

Once you have [performed a basic install](/getting-started/), you can secure {{ model.techName }} with more fine-grained options.
# Integration with DC/OS access controls

The {{ model.techName }} service may be run on DC/OS clusters in either permissive or strict mode.
DC/OS access controls must be used to restrict access to the {{ model.techName }} service when running on [strict mode](https://docs.mesosphere.com/latest/security/ent/#security-modes) clusters.
Configure the {{ model.techName }} service to authenticate itself using a certificate and to only grant permissions needed by the service.

## Create a service account

The following CLI commands create a service account named `{{ model.packageName }}-principal` and store its private certificate in a secret named `{{ model.packageName }}/service-private-key`:

```bash
dcos security org service-accounts keypair {{ model.packageName }}-private-key.pem {{ model.packageName }}-public-key.pem
dcos security org service-accounts create -p {{ model.packageName }}-public-key.pem -d "{{ model.packageName }} service account" {{ model.packageName }}-principal
dcos security secrets create-sa-secret --strict {{ model.packageName }}-private-key.pem {{ model.packageName }}-principal {{ model.packageName }}/service-private-key
```

## Add service permissions

Grant `{{ model.packageName }}-principal` the permissions required to run the {{ model.techName }} service:

```bash
dcos security org users grant {{ model.packageName }}-principal dcos:adminrouter:ops:ca:rw full
dcos security org users grant {{ model.packageName }}-principal dcos:adminrouter:ops:ca:ro full
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:agent:framework:role:slave_public read
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:framework:role:{{ model.packageName }}-role create
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:framework:role:slave_public read
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:framework:role:slave_public/{{ model.packageName }}-role read
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:framework:role:slave_public/{{ model.packageName }}-role create
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:reservation:principal:{{ model.packageName }}-principal delete
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:reservation:role:{{ model.packageName }}-role create
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:reservation:role:slave_public/{{ model.packageName }}-role create
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:task:user:nobody create
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:volume:principal:{{ model.packageName }}-principal delete
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:volume:role:{{ model.packageName }}-role create
dcos security org users grant {{ model.packageName }}-principal dcos:mesos:master:volume:role:slave_public/{{ model.packageName }}-role create
dcos security org users grant {{ model.packageName }}-principal dcos:secrets:default:/{{ model.packageName }}/\* full
dcos security org users grant {{ model.packageName }}-principal dcos:secrets:list:default:/{{ model.packageName }} read
```


## Install with custom options

You must identify for the {{ model.techName }} service which service account and certificate it should use for authentication.
Do so by installing the service with a custom configuration that sets the `service_account` field to the principal name and sets the `service_account_secret` field to the secret where the service certificate is stored.

Create a custom options file (`options.json`):

```json
{
  "service": {
    "service_account": "{{ model.packageName }}-principal",
    "service_account_secret": "{{ model.packageName }}/service-private-key"
  }
}
```

Then, install the service with custom options:

```bash
dcos package install {{ model.packageName }} --options=options.json
```
