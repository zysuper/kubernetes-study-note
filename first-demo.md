# 第一天

## 运行第一个 kubernete 程序

```sh
# kubectl run --generator=run/v1 is DEPRECATED and will be removed in a future version. Use kubectl run --generator=run-pod/v1 or kubectl create instead.
kubectl run kubia --image=nginx --port=80 --generator=run/v1
```

## 获取 pod 列表

```sh
kubectl get pods
```

## 创建 LB 服务对象

```sh
kubectl expose rc kubia --type=LoadBalancer --name kubia-http
```

## 列出服务

```sh
kubectl get services
```

minikube 不支持 LB，没有外部 IP，需要通过外部端口访问服务。

```sh
kubectl cluster-info
kubectl describe services kubia-http
```

输出会显示 Minikube node 的 IP 地址和 service 的 NodePort。然后使用这条命令访问应用：

```sh
curl <minikube-node-ip-address>:<service-node-port>
```