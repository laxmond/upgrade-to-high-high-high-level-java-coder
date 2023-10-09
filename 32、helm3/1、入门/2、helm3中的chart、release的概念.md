## helm中的chart、release的概念



#### 1、chart概念

chart 是 k8s 的资源包，采用 tar 格式，其中包含了部署一个服务的deployment、service、configmap、secret、ingress等资源配置文件



#### 2、release概念

使用 helm install 命令在 k8s 集群中部署的 Chart 称为 release