# calico-cni

![Version: 3.28.1](https://img.shields.io/badge/Version-3.28.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v3.28.1](https://img.shields.io/badge/AppVersion-v3.28.1-informational?style=flat-square)

This Helm chart has been created based on the reference minimalistic Calico deployment.
We do not use the Helm Chart Calico Operator provided by Tigera. This chart is based on a lightweigth Calico's configuration
manifest and it should work in most of the cases.

This chart is maintained by [Clastix Labs](https://github.com/clastix).

[Calico](https://github.com/projectcalico/calico) is a widely adopted, battle-tested open source networking and network security solution for Kubernetes.

Calico provides two major services for Cloud Native applications:

- Network connectivity between workloads.
- Network security policy enforcement between workloads.

This Helm chart has been created based on the reference minimalistic Calico deployment.
We do not use the Helm Chart Calico Operator provided by Tigera. This chart is based on a lightweigth Calico's configuration
manifest and it should work in most of the cases.

This chart is maintained by [Clastix Labs](https://github.com/clastix).

# Installing

```command
helm repo add clastix https://clastix.github.io/charts
helm repo update
helm install calico clastix/calico-cni -n kube-system
```

# Upgrading

```command
helm repo update
helm upgrade calico clastix/calico-cni -n kube-system --version <new_version>
```

## Customize the installation

There are two methods for specifying overrides of values during Chart installation: `--values` and `--set`.

The `--values` option is the preferred method because it allows you to keep your overrides in a YAML file, rather than specifying them all on the command line.
Create a copy of the YAML file `values.yaml` and add your overrides to it.

Specify your overrides file when you install the Chart:

        helm upgrade calico --install -n kube-system --values myvalues.yaml

The values in your overrides file `myvalues.yaml` will override their counterparts in the Chart's values.yaml file.
Any values in `values.yaml` that weren't overridden will keep their defaults.

If you only need to make minor customizations, you can specify them on the command line by using the `--set` option. For example:

        helm upgrade calico --install -n kube-system --set node.env.IP_AUTODETECTION_METHOD=kubernetes-internal-ip

Here the values you can override:

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| controllers.image.pullPolicy | string | `"IfNotPresent"` |  |
| controllers.image.repository | string | `"calico/kube-controllers"` |  |
| controllers.image.tag | string | `""` |  |
| controllers.nodeSelector."kubernetes.io/os" | string | `"linux"` |  |
| controllers.priorityClassName | string | `"system-cluster-critical"` |  |
| controllers.serviceAccount.annotations | object | `{}` |  |
| controllers.serviceAccount.create | bool | `true` |  |
| controllers.serviceAccount.name | string | `"calico-kube-controllers"` |  |
| controllers.tolerations[0].key | string | `"CriticalAddonsOnly"` |  |
| controllers.tolerations[0].operator | string | `"Exists"` |  |
| controllers.tolerations[1].effect | string | `"NoSchedule"` |  |
| controllers.tolerations[1].key | string | `"node-role.kubernetes.io/master"` |  |
| controllers.tolerations[2].effect | string | `"NoSchedule"` |  |
| controllers.tolerations[2].key | string | `"node-role.kubernetes.io/control-plane"` |  |
| fullnameOverride | string | `""` |  |
| imagePullSecrets | list | `[]` |  |
| nameOverride | string | `""` |  |
| node.env.CALICO_DISABLE_FILE_LOGGING | string | `"true"` |  |
| node.env.CALICO_IPV4POOL_IPIP | string | `"Never"` |  |
| node.env.CALICO_IPV4POOL_VXLAN | string | `"Never"` |  |
| node.env.CALICO_IPV6POOL_VXLAN | string | `"Never"` |  |
| node.env.CLUSTER_TYPE | string | `"k8s"` |  |
| node.env.DATASTORE_TYPE | string | `"kubernetes"` |  |
| node.env.FELIX_DEFAULTENDPOINTTOHOSTACTION | string | `"ACCEPT"` |  |
| node.env.FELIX_HEALTHENABLED | string | `"true"` |  |
| node.env.FELIX_IPV6SUPPORT | string | `"false"` |  |
| node.env.IP | string | `"autodetect"` |  |
| node.env.WAIT_FOR_DATASTORE | string | `"true"` |  |
| node.hostNetwork | bool | `true` |  |
| node.image.pullPolicy | string | `"IfNotPresent"` |  |
| node.image.repository | string | `"calico/node"` |  |
| node.image.tag | string | `""` |  |
| node.nodeSelector."kubernetes.io/os" | string | `"linux"` |  |
| node.priorityClassName | string | `"system-node-critical"` |  |
| node.serviceAccount.annotations | object | `{}` |  |
| node.serviceAccount.create | bool | `true` |  |
| node.serviceAccount.name | string | `"calico-node"` |  |
| node.tolerations[0].effect | string | `"NoSchedule"` |  |
| node.tolerations[0].operator | string | `"Exists"` |  |
| node.tolerations[1].key | string | `"CriticalAddonsOnly"` |  |
| node.tolerations[1].operator | string | `"Exists"` |  |
| node.tolerations[2].effect | string | `"NoExecute"` |  |
| node.tolerations[2].operator | string | `"Exists"` |  |

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Clastix Labs | <labs@clastix.io> |  |

## Source Code

* <https://github.com/clastix/calico-cni-minimal>
