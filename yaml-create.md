# 使用 yaml 文件创建 kube pod

## 获取 pod 的完整 yaml 配置

```sh
kubectl get pod kubia-zj68p -o yaml
```

[查看配置](./get-info.yaml)

## 通过 yaml 创建

```sh
kubectl create -f ./create.yaml
```

## 获取 pod 日志

```sh
kubectl logs kubia-manual
```

## 获取 pod 里容器日志

```sh
kubectl logs kubia-manual -c kubia
```

## 创建端口转发到 pod 中

```sh
kubectl port-forward kubia-manual 8888:8080
```

## 加标签

```sh
kubectl label po kubia-manual creation_method=manual # --overwrite 修改现有时加
```

## 列出标签列

```sh
kubectl get po -L creation_method,env
```

## 用标签来过滤

```sh
kubectl get po -l env
kubectl get po -l abc=xxx
kubectl get po -l !env
```

## 用标签分类 node 

```sh
kubectl label node minikube gpu=true 
```

## 获取有 gpu label 的节点

```zsh
➜  kubernetes kubectl get nodes -L gpu       
NAME       STATUS   ROLES    AGE     VERSION   GPU
minikube   Ready    master   2d10h   v1.15.0   true
```

## 节点选择部署
```yaml
spec:
  nodeSelector:
    gpu: "true"
```