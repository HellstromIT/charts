# paperless

![Version: 9.1.3](https://img.shields.io/badge/Version-9.1.3-informational?style=flat-square) ![AppVersion: 1.8.0](https://img.shields.io/badge/AppVersion-1.8.0-informational?style=flat-square)

Paperless - Index and archive all of your scanned paper documents

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/djjudas21/charts/issues/new/choose)**

## Source Code

* <https://github.com/paperless-ngx/paperless-ngx>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| `https://charts.bitnami.com/bitnami` | postgresql | 11.6.12 |
| `https://charts.bitnami.com/bitnami` | redis | 16.13.1 |
| `http://bjw-s.github.io/helm-charts/` | common | 4.5.2 |

## TL;DR

```console
helm repo add djjudas21 https://djjudas21.github.io/charts/
helm repo update
helm install paperless djjudas21/paperless
```

## Installing the Chart

To install the chart with the release name `paperless`

```console
helm install paperless djjudas21/paperless
```

## Uninstalling the Chart

To uninstall the `paperless` deployment

```console
helm uninstall paperless
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/bjw-s/helm-charts/blob/main/charts/library/common/values.yaml) from the [common library](https://github.com/bjw-s/helm-charts/tree/main/charts/library/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install paperless \
  --set env.TZ="America/New York" \
    djjudas21/paperless
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install paperless djjudas21/paperless -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/bjw-s/helm-charts/tree/main/charts/library/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env | object | See below | See the following files for additional environment variables: <https://github.com/paperless-ngx/paperless-ngx/tree/main/docker/compose/> <https://github.com/paperless-ngx/paperless-ngx/blob/main/paperless.conf.example> |
| env.COMPOSE_PROJECT_NAME | string | `"paperless"` | Project name |
| env.PAPERLESS_DBHOST | string | `nil` | Database host to use |
| env.PAPERLESS_OCR_LANGUAGE | string | `"eng"` | OCR languages to install |
| env.PAPERLESS_PORT | int | `8000` | Port to use |
| env.PAPERLESS_REDIS | string | `nil` | Redis to use |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"ghcr.io/paperless-ngx/paperless-ngx"` | image repository |
| image.tag | string | chart.appVersion | image tag |
| ingress.main | object | See values.yaml | Enable and configure ingress settings for the chart under this key. |
| persistence.consume | object | See values.yaml | Configure volume to monitor for new documents. |
| persistence.data | object | See values.yaml | Configure persistence for data. |
| persistence.export | object | See values.yaml | Configure export volume. |
| persistence.media | object | See values.yaml | Configure persistence for media. |
| postgresql | object | See values.yaml | Enable and configure postgresql database subchart under this key.    For more options see [postgresql chart documentation](https://github.com/bitnami/charts/tree/master/bitnami/postgresql) |
| redis | object | See values.yaml | Enable and configure redis subchart under this key.    For more options see [redis chart documentation](https://github.com/bitnami/charts/tree/master/bitnami/redis) |
| service | object | See values.yaml | Configures service settings for the chart. |

## Changelog

### Version 9.1.3

#### Added

N/A

#### Changed

* Upgraded `common` chart dependency to version 4.5.2

#### Fixed

N/A

### Older versions

A historical overview of changes can be found on [ArtifactHUB](https://artifacthub.io/packages/helm/djjudas21/paperless?modal=changelog)

## Support

* Open an [issue](https://github.com/djjudas21/charts/issues/new/choose)
