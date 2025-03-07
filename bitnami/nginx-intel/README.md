<!--- app-name: NGINX Open Source for Intel -->

# NGINX Open Source for Intel packaged by Bitnami

NGINX Open Source for Intel is a lightweight server, combined with cryptography acceleration for 3rd gen Xeon Scalable Processors (Ice Lake) to get a breakthrough performance improvement.

[Overview of NGINX Open Source for Intel](https://github.com/intel/asynch_mode_nginx)

Trademarks: This software listing is packaged by Bitnami. The respective trademarks mentioned in the offering are owned by the respective companies, and use of them does not imply any affiliation or endorsement.
                           
## TL;DR

```bash
$ helm repo add bitnami https://charts.bitnami.com/bitnami
$ helm install my-release bitnami/nginx-intel
```

## Introduction

Bitnami charts for Helm are carefully engineered, actively maintained and are the quickest and easiest way to deploy containers on a Kubernetes cluster that are ready to handle production workloads.

This chart bootstraps a [NGINX Open Source with Intel Optimizations](https://github.com/bitnami/bitnami-docker-nginx-intel) deployment on a [Kubernetes](https://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

Bitnami charts can be used with [Kubeapps](https://kubeapps.com/) for deployment and management of Helm Charts in clusters. This Helm chart has been tested on top of [Bitnami Kubernetes Production Runtime](https://kubeprod.io/) (BKPR). Deploy BKPR to get automated TLS certificates, logging and monitoring for your applications.

## Why use Intel optimized containers

Encryption is becoming pervasive with most organizations increasingly adopting encryption for application execution, data in flight, and data storage. Intel&reg; 3rd gen Xeon&reg; Scalable Processor (Ice Lake) cores and architecture, offers several new instructions for encryption acceleration. These new instructions, coupled with algorithmic and software innovations, deliver breakthrough performance for the industry's most widely deployed cryptographic ciphers.

This solution accelerates the processing of the Transport Layer Security (TLS) significantly by using built-in Intel crypto acceleration included in the latest Intel 3rd gen Xeon Scalable Processor (Ice Lake). For more information, refer to [Intel's documentation](https://www.intel.com/content/www/us/en/developer/articles/guide/nginx-https-with-crypto-ni-tuning-guide.html).

It requires a 3rd gen Xeon Scalable Processor (Ice Lake) to get a breakthrough performance improvement.

## Prerequisites

- Kubernetes 1.19+
- Helm 3.2.0

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm repo add bitnami https://charts.bitnami.com/bitnami
$ helm install my-release bitnami/nginx-intel
```

These commands deploy NGINX Open Source on the Kubernetes cluster in the default configuration.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Parameters

### Global parameters

| Name                      | Description                                     | Value |
| ------------------------- | ----------------------------------------------- | ----- |
| `global.imageRegistry`    | Global Docker image registry                    | `""`  |
| `global.imagePullSecrets` | Global Docker registry secret names as an array | `[]`  |


### Common parameters

| Name                | Description                                                                           | Value           |
| ------------------- | ------------------------------------------------------------------------------------- | --------------- |
| `nameOverride`      | String to partially override nginx.fullname template (will maintain the release name) | `""`            |
| `fullnameOverride`  | String to fully override nginx.fullname template                                      | `""`            |
| `kubeVersion`       | Force target Kubernetes version (using Helm capabilities if not set)                  | `""`            |
| `clusterDomain`     | Kubernetes Cluster Domain                                                             | `cluster.local` |
| `extraDeploy`       | Extra objects to deploy (value evaluated as a template)                               | `[]`            |
| `commonLabels`      | Add labels to all the deployed resources                                              | `{}`            |
| `commonAnnotations` | Add annotations to all the deployed resources                                         | `{}`            |


### NGINX parameters

| Name                 | Description                                                          | Value                 |
| -------------------- | -------------------------------------------------------------------- | --------------------- |
| `image.registry`     | NGINX image registry                                                 | `docker.io`           |
| `image.repository`   | NGINX image repository                                               | `bitnami/nginx-intel` |
| `image.tag`          | NGINX image tag (immutable tags are recommended)                     | `0.4.7-debian-10-r65` |
| `image.pullPolicy`   | NGINX image pull policy                                              | `IfNotPresent`        |
| `image.pullSecrets`  | Specify docker-registry secret names as an array                     | `[]`                  |
| `image.debug`        | Set to true if you would like to see extra information on logs       | `false`               |
| `hostAliases`        | Deployment pod host aliases                                          | `[]`                  |
| `command`            | Override default container command (useful when using custom images) | `[]`                  |
| `args`               | Override default container args (useful when using custom images)    | `[]`                  |
| `extraEnvVars`       | Extra environment variables to be set on NGINX containers            | `[]`                  |
| `extraEnvVarsCM`     | ConfigMap with extra environment variables                           | `""`                  |
| `extraEnvVarsSecret` | Secret with extra environment variables                              | `""`                  |


### NGINX deployment parameters

| Name                                    | Description                                                                               | Value   |
| --------------------------------------- | ----------------------------------------------------------------------------------------- | ------- |
| `replicaCount`                          | Number of NGINX replicas to deploy                                                        | `1`     |
| `podLabels`                             | Additional labels for NGINX pods                                                          | `{}`    |
| `podAnnotations`                        | Annotations for NGINX pods                                                                | `{}`    |
| `podAffinityPreset`                     | Pod affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`       | `""`    |
| `podAntiAffinityPreset`                 | Pod anti-affinity preset. Ignored if `affinity` is set. Allowed values: `soft` or `hard`  | `soft`  |
| `nodeAffinityPreset.type`               | Node affinity preset type. Ignored if `affinity` is set. Allowed values: `soft` or `hard` | `""`    |
| `nodeAffinityPreset.key`                | Node label key to match Ignored if `affinity` is set.                                     | `""`    |
| `nodeAffinityPreset.values`             | Node label values to match. Ignored if `affinity` is set.                                 | `[]`    |
| `affinity`                              | Affinity for pod assignment                                                               | `{}`    |
| `nodeSelector`                          | Node labels for pod assignment. Evaluated as a template.                                  | `{}`    |
| `tolerations`                           | Tolerations for pod assignment. Evaluated as a template.                                  | `{}`    |
| `priorityClassName`                     | Priority class name                                                                       | `""`    |
| `podSecurityContext.enabled`            | Enabled NGINX pods' Security Context                                                      | `false` |
| `podSecurityContext.fsGroup`            | Set NGINX pod's Security Context fsGroup                                                  | `1001`  |
| `podSecurityContext.sysctls`            | sysctl settings of the NGINX pods                                                         | `[]`    |
| `containerSecurityContext.enabled`      | Enabled NGINX containers' Security Context                                                | `false` |
| `containerSecurityContext.runAsUser`    | Set NGINX container's Security Context runAsUser                                          | `1001`  |
| `containerSecurityContext.runAsNonRoot` | Set NGINX container's Security Context runAsNonRoot                                       | `true`  |
| `containerPorts.http`                   | Sets http port inside NGINX container                                                     | `8080`  |
| `containerPorts.https`                  | Sets https port inside NGINX container                                                    | `8443`  |
| `resources.limits`                      | The resources limits for the NGINX container                                              | `{}`    |
| `resources.requests`                    | The requested resources for the NGINX container                                           | `{}`    |
| `livenessProbe.enabled`                 | Enable livenessProbe                                                                      | `true`  |
| `livenessProbe.initialDelaySeconds`     | Initial delay seconds for livenessProbe                                                   | `30`    |
| `livenessProbe.periodSeconds`           | Period seconds for livenessProbe                                                          | `10`    |
| `livenessProbe.timeoutSeconds`          | Timeout seconds for livenessProbe                                                         | `5`     |
| `livenessProbe.failureThreshold`        | Failure threshold for livenessProbe                                                       | `6`     |
| `livenessProbe.successThreshold`        | Success threshold for livenessProbe                                                       | `1`     |
| `readinessProbe.enabled`                | Enable readinessProbe                                                                     | `true`  |
| `readinessProbe.initialDelaySeconds`    | Initial delay seconds for readinessProbe                                                  | `5`     |
| `readinessProbe.periodSeconds`          | Period seconds for readinessProbe                                                         | `5`     |
| `readinessProbe.timeoutSeconds`         | Timeout seconds for readinessProbe                                                        | `3`     |
| `readinessProbe.failureThreshold`       | Failure threshold for readinessProbe                                                      | `3`     |
| `readinessProbe.successThreshold`       | Success threshold for readinessProbe                                                      | `1`     |
| `customLivenessProbe`                   | Override default liveness probe                                                           | `{}`    |
| `customReadinessProbe`                  | Override default readiness probe                                                          | `{}`    |
| `autoscaling.enabled`                   | Enable autoscaling for NGINX deployment                                                   | `false` |
| `autoscaling.minReplicas`               | Minimum number of replicas to scale back                                                  | `""`    |
| `autoscaling.maxReplicas`               | Maximum number of replicas to scale out                                                   | `""`    |
| `autoscaling.targetCPU`                 | Target CPU utilization percentage                                                         | `""`    |
| `autoscaling.targetMemory`              | Target Memory utilization percentage                                                      | `""`    |
| `extraVolumes`                          | Array to add extra volumes                                                                | `[]`    |
| `extraVolumeMounts`                     | Array to add extra mount                                                                  | `[]`    |
| `serviceAccount.create`                 | Enable creation of ServiceAccount for nginx pod                                           | `false` |
| `serviceAccount.name`                   | The name of the ServiceAccount to use.                                                    | `""`    |
| `serviceAccount.annotations`            | Annotations for service account. Evaluated as a template.                                 | `{}`    |
| `serviceAccount.autoMount`              | Auto-mount the service account token in the pod                                           | `false` |
| `sidecars`                              | Sidecar parameters                                                                        | `[]`    |
| `sidecarSingleProcessNamespace`         | Enable sharing the process namespace with sidecars                                        | `false` |
| `initContainers`                        | Extra init containers                                                                     | `[]`    |
| `pdb.create`                            | Created a PodDisruptionBudget                                                             | `false` |
| `pdb.minAvailable`                      | Min number of pods that must still be available after the eviction                        | `1`     |
| `pdb.maxUnavailable`                    | Max number of pods that can be unavailable after the eviction                             | `0`     |


### Custom NGINX application parameters

| Name                                       | Description                                                                                       | Value                  |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------- | ---------------------- |
| `cloneStaticSiteFromGit.enabled`           | Get the server static content from a Git repository                                               | `false`                |
| `cloneStaticSiteFromGit.image.registry`    | Git image registry                                                                                | `docker.io`            |
| `cloneStaticSiteFromGit.image.repository`  | Git image repository                                                                              | `bitnami/git`          |
| `cloneStaticSiteFromGit.image.tag`         | Git image tag (immutable tags are recommended)                                                    | `2.35.1-debian-10-r63` |
| `cloneStaticSiteFromGit.image.pullPolicy`  | Git image pull policy                                                                             | `IfNotPresent`         |
| `cloneStaticSiteFromGit.image.pullSecrets` | Specify docker-registry secret names as an array                                                  | `[]`                   |
| `cloneStaticSiteFromGit.repository`        | Git Repository to clone static content from                                                       | `""`                   |
| `cloneStaticSiteFromGit.branch`            | Git branch to checkout                                                                            | `""`                   |
| `cloneStaticSiteFromGit.interval`          | Interval for sidecar container pull from the Git repository                                       | `60`                   |
| `cloneStaticSiteFromGit.gitClone.command`  | Override default container command for git-clone-repository                                       | `[]`                   |
| `cloneStaticSiteFromGit.gitClone.args`     | Override default container args for git-clone-repository                                          | `[]`                   |
| `cloneStaticSiteFromGit.gitSync.command`   | Override default container command for git-repo-syncer                                            | `[]`                   |
| `cloneStaticSiteFromGit.gitSync.args`      | Override default container args for git-repo-syncer                                               | `[]`                   |
| `cloneStaticSiteFromGit.extraEnvVars`      | Additional environment variables to set for the in the containers that clone static site from git | `[]`                   |
| `cloneStaticSiteFromGit.extraVolumeMounts` | Add extra volume mounts for the Git containers                                                    | `[]`                   |
| `serverBlock`                              | Custom server block to be added to NGINX configuration                                            | `""`                   |
| `existingServerBlockConfigmap`             | ConfigMap with custom server block to be added to NGINX configuration                             | `""`                   |
| `staticSiteConfigmap`                      | Name of existing ConfigMap with the server static site content                                    | `""`                   |
| `staticSitePVC`                            | Name of existing PVC with the server static site content                                          | `""`                   |


### Traffic Exposure parameters

| Name                            | Description                                                                                                                      | Value                    |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ------------------------ |
| `service.type`                  | Service type                                                                                                                     | `LoadBalancer`           |
| `service.port`                  | Service HTTP port                                                                                                                | `80`                     |
| `service.httpsPort`             | Service HTTPS port                                                                                                               | `443`                    |
| `service.nodePorts`             | Specify the nodePort(s) value(s) for the LoadBalancer and NodePort service types.                                                | `{}`                     |
| `service.targetPort`            | Target port reference value for the Loadbalancer service types can be specified explicitly.                                      | `{}`                     |
| `service.loadBalancerIP`        | LoadBalancer service IP address                                                                                                  | `""`                     |
| `service.annotations`           | Service annotations                                                                                                              | `{}`                     |
| `service.externalTrafficPolicy` | Enable client source IP preservation                                                                                             | `Cluster`                |
| `ingress.enabled`               | Set to true to enable ingress record generation                                                                                  | `false`                  |
| `ingress.pathType`              | Ingress path type                                                                                                                | `ImplementationSpecific` |
| `ingress.apiVersion`            | Force Ingress API version (automatically detected if not set)                                                                    | `""`                     |
| `ingress.hostname`              | Default host for the ingress resource                                                                                            | `nginx.local`            |
| `ingress.path`                  | The Path to Nginx. You may need to set this to '/*' in order to use this with ALB ingress controllers.                           | `/`                      |
| `ingress.annotations`           | Additional annotations for the Ingress resource. To enable certificate autogeneration, place here your cert-manager annotations. | `{}`                     |
| `ingress.tls`                   | Create TLS Secret                                                                                                                | `false`                  |
| `ingress.extraHosts`            | The list of additional hostnames to be covered with this ingress record.                                                         | `[]`                     |
| `ingress.extraPaths`            | Any additional arbitrary paths that may need to be added to the ingress under the main host.                                     | `[]`                     |
| `ingress.extraTls`              | The tls configuration for additional hostnames to be covered with this ingress record.                                           | `[]`                     |
| `ingress.secrets`               | If you're providing your own certificates, please use this to add the certificates as secrets                                    | `[]`                     |
| `healthIngress.enabled`         | Set to true to enable health ingress record generation                                                                           | `false`                  |
| `healthIngress.pathType`        | Ingress path type                                                                                                                | `ImplementationSpecific` |
| `healthIngress.hostname`        | When the health ingress is enabled, a host pointing to this will be created                                                      | `example.local`          |
| `healthIngress.annotations`     | Additional annotations for the Ingress resource. To enable certificate autogeneration, place here your cert-manager annotations. | `{}`                     |
| `healthIngress.tls`             | Enable TLS configuration for the hostname defined at `healthIngress.hostname` parameter                                          | `false`                  |
| `healthIngress.extraHosts`      | The list of additional hostnames to be covered with this health ingress record                                                   | `[]`                     |
| `healthIngress.extraTls`        | TLS configuration for additional hostnames to be covered                                                                         | `[]`                     |
| `healthIngress.secrets`         | TLS Secret configuration                                                                                                         | `[]`                     |


### Metrics parameters

| Name                                   | Description                                                                                 | Value                    |
| -------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------ |
| `metrics.enabled`                      | Start a Prometheus exporter sidecar container                                               | `false`                  |
| `metrics.port`                         | NGINX Container Status Port scraped by Prometheus Exporter                                  | `""`                     |
| `metrics.image.registry`               | NGINX Prometheus exporter image registry                                                    | `docker.io`              |
| `metrics.image.repository`             | NGINX Prometheus exporter image repository                                                  | `bitnami/nginx-exporter` |
| `metrics.image.tag`                    | NGINX Prometheus exporter image tag (immutable tags are recommended)                        | `0.10.0-debian-10-r98`   |
| `metrics.image.pullPolicy`             | NGINX Prometheus exporter image pull policy                                                 | `IfNotPresent`           |
| `metrics.image.pullSecrets`            | Specify docker-registry secret names as an array                                            | `[]`                     |
| `metrics.podAnnotations`               | Additional annotations for NGINX Prometheus exporter pod(s)                                 | `{}`                     |
| `metrics.securityContext.enabled`      | Enabled NGINX Exporter containers' Security Context                                         | `false`                  |
| `metrics.securityContext.runAsUser`    | Set NGINX Exporter container's Security Context runAsUser                                   | `1001`                   |
| `metrics.service.port`                 | NGINX Prometheus exporter service port                                                      | `9113`                   |
| `metrics.service.annotations`          | Annotations for the Prometheus exporter service                                             | `{}`                     |
| `metrics.resources.limits`             | The resources limits for the NGINX Prometheus exporter container                            | `{}`                     |
| `metrics.resources.requests`           | The requested resources for the NGINX Prometheus exporter container                         | `{}`                     |
| `metrics.serviceMonitor.enabled`       | Creates a Prometheus Operator ServiceMonitor (also requires `metrics.enabled` to be `true`) | `false`                  |
| `metrics.serviceMonitor.namespace`     | Namespace in which Prometheus is running                                                    | `""`                     |
| `metrics.serviceMonitor.interval`      | Interval at which metrics should be scraped.                                                | `""`                     |
| `metrics.serviceMonitor.scrapeTimeout` | Timeout after which the scrape is ended                                                     | `""`                     |
| `metrics.serviceMonitor.selector`      | Prometheus instance selector labels                                                         | `{}`                     |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```bash
$ helm install my-release \
  --set imagePullPolicy=Always \
    bitnami/nginx-intel
```

The above command sets the `imagePullPolicy` to `Always`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install my-release -f values.yaml bitnami/nginx-intel
```

> **Tip**: You can use the default [values.yaml](values.yaml)

## Configuration and installation details

### [Rolling VS Immutable tags](https://docs.bitnami.com/containers/how-to/understand-rolling-tags-containers/)

It is strongly recommended to use immutable tags in a production environment. This ensures your deployment does not change automatically if the same tag is updated with a different image.

Bitnami will release a new chart updating its containers if a new version of the main container, significant changes, or critical vulnerabilities exist.

### Use a different NGINX version

To modify the application version used in this chart, specify a different version of the image using the `image.tag` parameter and/or a different repository using the `image.repository` parameter. Refer to the [chart documentation for more information on these parameters and how to use them with images from a private registry](https://docs.bitnami.com/kubernetes/infrastructure/nginx/configuration/change-image-version/).

### Deploying your custom web application

The NGINX chart allows you to deploy a custom web application using one of the following methods:

- Cloning from a git repository: Set `cloneStaticSiteFromGit.enabled` to `true` and set the repository and branch using the `cloneStaticSiteFromGit.repository` and  `cloneStaticSiteFromGit.branch` parameters. A sidecar will also pull the latest changes in an interval set by `cloneStaticSitesFromGit.interval`.
- Providing a ConfigMap: Set the `staticSiteConfigMap` value to mount a ConfigMap in the NGINX html folder.
- Using an existing PVC: Set the `staticSitePVC` value to mount an PersistentVolumeClaim with the static site content.

You can deploy a example web application using git deploying the chart with the following parameters:

```console
cloneStaticSiteFromGit.enabled=true
cloneStaticSiteFromGit.repository=https://github.com/mdn/beginner-html-site-styled.git
cloneStaticSiteFromGit.branch=master
```

### Providing a custom server block

This helm chart supports using custom custom server block for NGINX to use.

You can use the `serverBlock` value to provide a custom server block for NGINX to use. To do this, create a values files with your server block and install the chart using it:

```yaml
serverBlock: |-
  server {
    listen 0.0.0.0:8080;
    location / {
      return 200 "hello!";
    }
  }
```

> Warning: The above example is not compatible with enabling Prometheus metrics since it affects the `/status` endpoint.

In addition, you can also set an external ConfigMap with the configuration file. This is done by setting the `existingServerBlockConfigmap` parameter. Note that this will override the previous option.

### Adding extra environment variables

In case you want to add extra environment variables (useful for advanced operations like custom init scripts), you can use the `extraEnvVars` property.

```yaml
extraEnvVars:
  - name: LOG_LEVEL
    value: error
```

Alternatively, you can use a ConfigMap or a Secret with the environment variables. To do so, use the `extraEnvVarsCM` or the `extraEnvVarsSecret` values.

### Setting Pod's affinity

This chart allows you to set your custom affinity using the `affinity` parameter. Find more information about Pod's affinity in the [kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#affinity-and-anti-affinity).

As an alternative, you can use of the preset configurations for pod affinity, pod anti-affinity, and node affinity available at the [bitnami/common](https://github.com/bitnami/charts/tree/master/bitnami/common#affinity) chart. To do so, set the `podAffinityPreset`, `podAntiAffinityPreset`, or `nodeAffinityPreset` parameters.

### Deploying extra resources

There are cases where you may want to deploy extra objects, such a ConfigMap containing your app's configuration or some extra deployment with a micro service used by your app. For covering this case, the chart allows adding the full specification of other objects using the `extraDeploy` parameter.

### Ingress

This chart provides support for ingress resources. If you have an ingress controller installed on your cluster, such as [nginx-ingress-controller](https://github.com/bitnami/charts/tree/master/bitnami/nginx-intel-ingress-controller) or [contour](https://github.com/bitnami/charts/tree/master/bitnami/contour) you can utilize the ingress controller to serve your application.

To enable ingress integration, please set `ingress.enabled` to `true`.

#### Hosts

Most likely you will only want to have one hostname that maps to this NGINX installation. If that's your case, the property `ingress.hostname` will set it. However, it is possible to have more than one host. To facilitate this, the `ingress.extraHosts` object can be specified as an array. You can also use `ingress.extraTLS` to add the TLS configuration for extra hosts.

For each host indicated at `ingress.extraHosts`, please indicate a `name`, `path`, and any `annotations` that you may want the ingress controller to know about.

For annotations, please see [this document](https://github.com/kubernetes/ingress-nginx/blob/master/docs/user-guide/nginx-configuration/annotations.md). Not all annotations are supported by all ingress controllers, but this document does a good job of indicating which annotation is supported by many popular ingress controllers.

## Troubleshooting

Find more information about how to deal with common errors related to Bitnami's Helm charts in [this troubleshooting guide](https://docs.bitnami.com/general/how-to/troubleshoot-helm-chart-issues).

## Upgrading

### To 1.0.0

This major release no longer uses the bitnami/nginx-ldap-auth-daemon container as a dependency since its upstream project is not actively maintained.

*2022-04-12 edit*:

Bitnami���s NGINX Intel Helm chart from version 0.0.1 to 0.1.11 includes a `ldapDaemon.enabled` option **disabled by default** that allows to configure it with the [bitnami-docker-nginx-ldap-auth-daemon](https://github.com/bitnami/bitnami-docker-nginx-ldap-auth-daemon) following [NGINX���s reference implementation](https://www.nginx.com/blog/nginx-plus-authenticate-users/).

On 9 April 2022, security vulnerabilities in the [NGINX LDAP reference implementation](https://github.com/nginxinc/nginx-ldap-auth) were publicly shared. **Although the deprecation of this container from the Bitnami catalog was not related to this security issue, [here](https://docs.bitnami.com/general/security/security-2022-04-12/) you can find more information from the Bitnami security team.**

## Bitnami Kubernetes Documentation

Bitnami Kubernetes documentation is available at [https://docs.bitnami.com/](https://docs.bitnami.com/). You can find there the following resources:

- [Documentation for NGINX Helm chart](https://docs.bitnami.com/kubernetes/infrastructure/nginx/)
- [Get Started with Kubernetes guides](https://docs.bitnami.com/kubernetes/)
- [Bitnami Helm charts documentation](https://docs.bitnami.com/kubernetes/apps/)
- [Kubernetes FAQs](https://docs.bitnami.com/kubernetes/faq/)
- [Kubernetes Developer guides](https://docs.bitnami.com/tutorials/)

## License

Copyright &copy; 2022 Bitnami

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.