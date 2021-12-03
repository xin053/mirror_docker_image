# mirror_docker_image

![github action](https://github.com/xin053/mirror_docker_image/actions/workflows/mirror_docker_image.yml/badge.svg)

[github](https://github.com/xin053/mirror_docker_image)

[中文文档](https://github.com/xin053/mirror_docker_image/blob/main/README_zh.md)

Synchronize the `docker` image from one registry to another through `github action`. For example, synchronize the specified docker image under `gcr.io` to `docker.io`.

## Usage

Open a new `issue`, then use the image name to be synchronized as title (**The image name needs to be a full name, which means `registry` and `tag` cannot be omitted**), the content of `issue` can be empty.

For example: open a new `issue` with title `k8s.gcr.io/kube-state-metrics/kube-state-metrics:latest`, Then the github action will automatically pull the image and push it to the [`xin053` repository](hub.docker.com/u/xin053), then you can use `docker pull xin053/kube-state-metrics:latest` command to pull the image.

You can view the synchronized docker images through the link below:

[hub.docker.com/u/xin053](hub.docker.com/u/xin053)

![](https://github.com/xin053/mirror_docker_image/blob/main/images/1.png)

## `secrets` supported by `action`

|        key        |                value                 |
| :---------------: | :----------------------------------: |
| `SOURCE_USERNAME` |     username of source registry      |
| `SOURCE_PASSWORD` |     password of source registry      |
| `TARGET_REGISTRY` | target registry, default `docker.io` |
| `TARGET_USERNAME` |       username of `docker hub`       |
| `TARGET_USERNAME` | password or `token` of `docker hub`  |

## If the source registry needs to log in

After `fork` this github repository, add the following `secrets`:

|        key        |                value                |
| :---------------: | :---------------------------------: |
| `SOURCE_USERNAME` |     username of source registry     |
| `SOURCE_PASSWORD` |     password of source registry     |
| `TARGET_USERNAME` |      username of `docker hub`       |
| `TARGET_USERNAME` | password or `token` of `docker hub` |


**Remarks: If you log in with token on docker hub, you cannot modify the description of the synchronized docker images**

For details: [https://github.com/peter-evans/dockerhub-description/issues/10](https://github.com/peter-evans/dockerhub-description/issues/10)

## If the target registry is not `docker.io`

After `fork` this github repository, add the following `secrets`:

|        key        |               value                |
| :---------------: | :--------------------------------: |
| `TARGET_REGISTRY` | target registry, such as `ghcr.io` |
| `TARGET_USERNAME` |    username of target registry     |
| `TARGET_USERNAME` |    password of target registry     |

## Project stats

![Alt](https://repobeats.axiom.co/api/embed/11e8bb6f504f02fca58a38db2527c314b8a0b9c4.svg "Repobeats analytics image")
