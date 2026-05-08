# ParFlow Docker 环境中文配置指南

本镜像基于 Ubuntu 22.04，编译并安装了[同时耦合 CLM 与 CoLM 的 ParFlow 版本](https://github.com/aureliayang/parflow)，同时安装了jupyterlab，matplotlib，numpy，pandas，xarray，netCDF4用于数据处理与可视化分析的Python基础依赖。

更多有关ParFlow教程可以关注我们的公众号： **ParFlow Community**

![ParFlow Community](ParFlowCommunity.jpg)

---

## 环境要求

- 若未安装Docker，请先安装 [Docker Desktop](https://www.docker.com/products/docker-desktop/)

---

## 快速开始

### 第一步：拉取镜像

```bash
docker pull parflowcommunity/parflow-docker-cn:v1.0
```

> **Apple Silicon Mac 用户（M芯片）**：本镜像仅提供 amd64 架构，拉取时需指定平台，否则会报错：
> ```bash
> docker pull --platform linux/amd64 parflowcommunity/parflow-docker-cn:v1.0
> ```

### 第二步：启动容器

在终端中先进入你的数据目录，再运行容器（`./` 表示当前目录，适用于所有平台）。

**Windows 用户请使用 PowerShell，不要使用 CMD。**

```bash
cd /你的数据目录路径
docker run -d --rm \
  -v ./:/workspace \
  -p 8888:8888 \
  parflowcommunity/parflow-docker-cn:v1.0
```

### 第三步：打开 JupyterLab

浏览器访问：

```
http://localhost:8888
```

访问密码（token）：

```
parflow2026
```

---

## 运行ParFlow

进入 JupyterLab 后，打开终端，执行：

```bash
cd /workspace
python your_ParFlow_examples.py
```

或在 Notebook 中直接运行对应的 `.ipynb` 文件。

---

## 停止容器

```bash
docker ps                          # 查看正在运行的容器，找到容器 ID
docker stop <容器ID>
```

由于启动时使用了 `--rm` 参数，容器停止后会自动删除，不会留下残留。

---
