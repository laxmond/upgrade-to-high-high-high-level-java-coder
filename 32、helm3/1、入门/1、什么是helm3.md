## 什么是helm3

helm是k8s的资源包管理工具。它使我们操作的对象不再是单个资源，而是一个实体。比如我们需要一个负载均衡的 web 服务，如果不使用 helm，我们需要写 deployment，service 和 ingress 才可以让集群外部的客户使用。但是如果使用 helm，直接使用一个 install 命令便可以实现相同的功能。

helm的功能类似于centos的yum、php的composer、java的mvn、python的pip。

