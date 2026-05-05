# ParFlow Docker 环境中文配置指南

本镜像基于 Ubuntu 22.04，集成了 ParFlow 及其依赖（Hypre、OpenMPI、CLM），并内置 JupyterLab。

更多有关ParFlow教程可以关注我们的公众号： **ParFlow Community**
---

## 环境要求

- 已安装 [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- 根据用户的网络环境，需要使用科学上网，并打开代理软件的Tun模式。

---

## 快速开始

### 第一步：拉取镜像

```bash
docker pull tangzy36/parflow-docker:v1.0
```

### 第二步：启动容器

将本地的目录挂载到容器的 `/workspace`：

```bash
docker run -d --rm \
  -v /path/to/data:/workspace \
  -p 8888:8888 \
  tangzy36/parflow-docker:v1.0
```

**Windows 用户**请将路径替换为 Windows 格式，例如：

```bash
docker run -d --rm \
  -v C:/Users/yourname/data:/workspace \
  -p 8888:8888 \
  tangzy36/parflow-docker:v1.0
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
