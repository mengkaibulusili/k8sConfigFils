# 介绍
这是一个 k8s 集群 的 dashbroad 控制面板
# 使用命令

## 下载 并 创建 服务 

```bash
kubectl  apply -f  recommended.yaml
```

## 删除服务
```bash
kubectl  delete -f  recommended.yaml
```

## 创建用户

```bash
kubectl  apply -f  adduser.yaml
```

## 绑定 用户和服务
```bash
kubectl  apply -f  ClusterRoleBinding.yaml
```

## 查看 token

！！！！ 记住 token
```bash 
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | sls admin-user | ForEach-Object { $_ -Split '\s+' } | Select -First 1)

output：
Name:         admin-user-token-h9lvx
Namespace:    kubernetes-dashboard
Labels:       <none>
Annotations:  kubernetes.io/service-account.name: admin-user
              kubernetes.io/service-account.uid: 61e3d84e-b871-469f-abb7-b50c8a325d76

Type:  kubernetes.io/service-account-token

Data
====
token:      eyJhbGciOiJ
ca.crt:     1025 bytes
namespace:  20 bytes

```



## 访问 web

```bash
kubectl  proxy
访问 web 服务即可
```

http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/

输入上一步的 token

