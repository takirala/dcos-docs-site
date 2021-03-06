---
layout: layout.pug
navigationTitle:  Secrets
title: Secrets
menuWeight: 60
excerpt: Understanding the Secret Store

enterprise: true
---
<!-- The source repository for this topic is https://github.com/dcos/dcos-docs-site -->


The DC/OS Enterprise Secret Store is a place to secure sensitive information like database passwords, API tokens, and private keys. Storing secrets in secret paths allows you to restrict which services can retrieve the value.

[Authorized Marathon services](/mesosphere/dcos/1.12//security/ent/#spaces) can retrieve the secrets at deployment and store their values under environment variables. In addition, the [Secrets API](/mesosphere/dcos/1.12/security/ent/secrets/secrets-api/) allows you to [seal](/mesosphere/dcos/1.12/security/ent/secrets/seal-store/) and [unseal](/mesosphere/dcos/1.12/security/ent/secrets/unseal-store/) the Secret Store.


Find more information about secrets in the [Permissions Reference](/mesosphere/dcos/1.12/security/ent/perms-reference/#secrets) section. Also, learn more about the functionality to backup and restore secrets easily from this [blog](https://mesosphere.com/blog/backup-restore-secrets/).
