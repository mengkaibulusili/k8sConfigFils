# 介绍
这是一个 nginx 集群副本
包含了 创建脚本，扩容脚本 ， 以及 对外开放服务脚本
# 使用命令

## 创建服务 2个 副本集

```bash
kubectl  apply -f  deployment.yaml
```

## 对外 开放 服务
开放到 30100 端口

```bash
kubectl  apply -f  service.yaml
```

## 动态扩容 4个 副本集
```bash
kubectl  apply -f  deployment-scale.yaml
```

## 删除服务
## 删除服务
```bash
kubectl  delete -f  deployment.yaml
```