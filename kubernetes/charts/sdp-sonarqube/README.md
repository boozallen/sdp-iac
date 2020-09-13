# SDP SonarQube

[SonarQube](https://www.sonarqube.org/) is an open sourced code quality scanning tool.
This chart is a modification of the Sonarqube helm chart for deployment with the Solutions Delivery Platform

## Introduction

This chart bootstraps a SonarQube instance with a PostgreSQL database.

The default login is admin/admin.


## Configuration

The following table lists the configurable parameters of the Sonarqube chart and their default values.

| Parameter                                   | Description                               | Default                                    |
| ------------------------------------------  | ----------------------------------------  | -------------------------------------------|
| `image.repository`                          | image repository                          | `sonarqube`                                |
| `image.tag`                                 | `sonarqube` image tag.                    | `7.8-community`                                        |
| `image.pullPolicy`                          | Image pull policy                         | `IfNotPresent`                             |
| `image.pullSecret`                          | imagePullSecret to use for private repository      |                                   |
| `replicaCount`                                   | Configures number of pods of Sonarqube to be deployed           | `1`       | 
| `username`                                   | username to be configured on sonarqube for pipelines to use           | `sonar`       | 
| `password`                                   | pasword to be configured on sonarqube for pipelines to use           | `sonar`       |
| `patch`                   |Apply patch (needed for upstream docker image of sonarqube:6.7) |  `true`                                 |
| `securityContext.fsGroup`                   | Group applied to mounted directories/files|  `999`                                     |
| `securityContext.runAsUser`                   | userid to run sonarqube server as |  `999`                                     |
| `securityContext.runAsGroup`                   | groupid to run sonarqube server as |  `999`                                     |
| `scc.create`                   | Create Security Context Constraint |  `false`                                     |
| `serviceAccount.create`                   | Create Sonarqube service account |  `true`                                     |
| `serviceAccount.name`                   | Name of Sonarqube service account |  `sonarsa`                                     
| `ingress.enabled`                           | Flag for enabling ingress                 | true                                      |
| `ingress.labels`                            | Ingress additional labels                 | `{}`                                       |
| `ingress.hosts[0].name`                     | Hostname to your SonarQube installation   | `sonar.sdp.com`                   |
| `ingress.hosts[0].path`                     | Path within the URL structure             | /                                          |
| `ingress.tls`                               | Ingress secrets for TLS certificates      | `[]`                                       |
| `livenessProbe.sonarWebContext`             | SonarQube web context for livenessProbe   | /                                          |
| `readinessProbe.sonarWebContext`            | SonarQube web context for readinessProbe  | /                                          |
| `service.type`                              | Kubernetes service type                   | `LoadBalancer`                             |
| `service.labels`                            | Kubernetes service labels                 | None                                       |
| `service.annotations`                       | Kubernetes service annotations            | None                                       |
| `service.loadBalancerSourceRanges`          | Kubernetes service LB Allowed inbound IP addresses | 0.0.0.0/0                            |
| `service.loadBalancerIP`                    | Kubernetes service LB Optional fixed external IP   | None                                       |
| `persistence.enabled`                       | Flag for enabling persistent storage      | false                                      |
| `persistence.annotations`                   | Kubernetes pvc annotations                | `{}`                                      |
| `persistence.existingClaim`                 | Do not create a new PVC but use this one  | None                                       |
| `persistence.storageClass`                  | Storage class to be used                  | "-"                                        |
| `persistence.accessMode`                    | Volumes access mode to be set             | `ReadWriteOnce`                            |
| `persistence.size`                          | Size of the volume                        | None                                     |
| `sonarProperties`                           | Custom `sonar.properties` file            | None                                       |
| `database.type`                             | Set to "mysql" to use mysql database       | `postgresql`|
| `postgresql.enabled`                        | Set to `false` to use external server / mysql database     | `true`                                     |
| `postgresql.postgresServer`                 | Hostname of the external Postgresql server| `null`                                     |
| `postgresql.postgresPasswordSecret`         | Secret containing the password of the external Postgresql server | `null`              |
| `postgresql.postgresUser`                   | Postgresql database user                  | `sonarUser`                                |
| `postgresql.postgresPassword`               | Postgresql database password              | `sonarPass`                                |
| `postgresql.postgresDatabase`               | Postgresql database name                  | `sonarDB`                                  |
| `postgresql.service.port`                   | Postgresql port                           | `5432`                                     |
| `annotations`                               | Sonarqube Pod annotations                 | `{}`                                       |
| `resources`                                 | Sonarqube Pod resource requests & limits  | `{}`                                       |
| `affinity`                                  | Node / Pod affinities                     | `{}`                                       |
| `nodeSelector`                              | Node labels for pod assignment            | `{}`                                       |
| `hostAliases`                               | Aliases for IPs in /etc/hosts             | `[]`                                       |
| `tolerations`                               | List of node taints to tolerate           | `[]`                                       |
| `plugins.install`                           | List of plugins to install                | `[]`                                       |
| `plugins.resources`                         | Plugin Pod resource requests & limits     | `{}`                                       |
| `plugins.initContainerImage`                | Change init container image               | `[]`                                       |
| `plugins.deleteDefaultPlugins`              | Remove default plugins and use plugins.install list | `[]`                             |
| `podLabels`                                 | Map of labels to add to the pods          | `{}`                                       |
| `route.enabled`                                 | Enable Openshift route          | `true`                                       |
| `route.path`                                 | Host Path for Openshift route         | `sonarqube.sdp.com`                          |
| `jenkins.masterNamespace`                                 | Namespace of the Jenkins master         | `default`                          |
