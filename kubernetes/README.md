--------------------------------------
SDP Generic k8s Deployment Helm Chart
--------------------------------------
## Pre-requisites

helm package manager (with helm and tiller components) must be installed and functional 
(This chart has been tested with helm version 2.16.1 and is not been tested with versions above 2.16.1 or with Helm 3)

## Chart Details

This chart will do the following:

* Install a Jenkins Master in the default or existing custom namespace
* Optionally install persistent Jenkins agents
* Optionally install sonarqube server


## Installing the Chart

Note: Customize values.yaml for sdp sdp-jenkins sdp-sonarqube based on the target deployment environment 

To install the chart with the release name `my-release`into an existing namespace 'sdp-namespace':

```bash
$ helm install --name my-release sdp/ --namespace sdp-namespace
```

To uninstall the chart with the release name `my-release` installed in namespace 'sdp-namespace':

```bash
$ helm delete --purge  my-release  
$ kubectl delete secret sdp-jenkins-secret --namespace 'sdp-namespace'
```


## Configuration

The following tables list the configurable parameters of the Jenkins chart and their default values. The chart can be customized by modifying these values.

### Jenkins Master

| Parameter                         | Description                          | Default                                   |
| --------------------------------- | ------------------------------------ | ----------------------------------------- |
| `sdp-jenkins.persistentSlaveEnabled`          | Deploy persistent Jenkins agents     | `true`                                    |
| `sdp-jenkins.numAgents `                     | Number of Agents to be deployed      | `1`                                       |
| `sdp-sonarqube.enabled`                    | Deploy Sonarqube  | `true`                                 |

