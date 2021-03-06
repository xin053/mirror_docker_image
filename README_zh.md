# mirror_docker_image

![github action](https://github.com/xin053/mirror_docker_image/actions/workflows/mirror_docker_image.yml/badge.svg)

[github](https://github.com/xin053/mirror_docker_image)

[english document](https://github.com/xin053/mirror_docker_image/blob/main/README.md)

利用 `github action` 将 `docker` 镜像从一个仓库同步到另一个仓库。例如，将 `gcr.io` 下的指定镜像同步到 `docker.io` 中。

## 使用

创建一个新的 `issue`, `issue` 标题填写需要同步的镜像(**镜像名称需要是完整名称,不能省略 `registry` 与 `tag`**), `issue` 内容可为空

例如: 创建的 `issue` 标题为 `k8s.gcr.io/kube-state-metrics/kube-state-metrics:latest`, 则 github action 会自动拉取该镜像并推送到 `docker hub` 的 [`xin053`](https://hub.docker.com/u/xin053) 用户下, 之后可通过 `docker pull xin053/kube-state-metrics:latest` 拉取该镜像

通过下面的链接可以查看同步过的镜像:

[https://hub.docker.com/u/xin053](https://hub.docker.com/u/xin053)

![](https://github.com/xin053/mirror_docker_image/blob/main/images/1.png)

## 自定义 `action`

`fork` 该仓库之后, 并到仓库 `settings` 页面中的 `Features` 中勾选 `Issues`, 并且在 `Actions` 页面启用 `github actions`, 然后按照需要添加相应的 `secrets` 后, 即可在自己 `fork` 的仓库中创建 `issue` 来同步 `docker` 镜像了

## `action` 支持的 `secrets`

|         key         |              value              |
| :-----------------: | :-----------------------------: |
|  `SOURCE_USERNAME`  |          源仓库用户名           |
|  `SOURCE_PASSWORD`  |           源仓库密码            |
|  `TARGET_REGISTRY`  | 目标仓库地址,默认为 `docker.io` |
| `TARGET_REPOSITORY` |      目标项目地址,默认为空      |
|  `TARGET_USERNAME`  |       `docker hub` 用户名       |
|  `TARGET_PASSWORD`  |   `docker hub` 密码或 `token`   |

## 如果源仓库需要登录

`fork` 该仓库后, 添加如下 `secrets`

|        key        |            value            |
| :---------------: | :-------------------------: |
| `SOURCE_USERNAME` |        源仓库用户名         |
| `SOURCE_PASSWORD` |         源仓库密码          |
| `TARGET_USERNAME` |     `docker hub` 用户名     |
| `TARGET_PASSWORD` | `docker hub` 密码或 `token` |


**备注: docker hub 如果使用 token 登录, 则无法修改 docker hub 对应仓库的描述**

详见: [https://github.com/peter-evans/dockerhub-description/issues/10](https://github.com/peter-evans/dockerhub-description/issues/10)

## 如果目标仓库不是 `docker.io`

`fork` 该仓库后, 添加如下 `secrets`

|         key         |           value           |
| :-----------------: | :-----------------------: |
|  `TARGET_REGISTRY`  | 目标仓库地址,如 `ghcr.io` |
| `TARGET_REPOSITORY` |  目标项目地址,如 `test`   |
|  `TARGET_USERNAME`  |      目标仓库用户名       |
|  `TARGET_PASSWORD`  |       目标仓库密码        |

## 项目统计

![Alt](https://repobeats.axiom.co/api/embed/11e8bb6f504f02fca58a38db2527c314b8a0b9c4.svg "Repobeats analytics image")
