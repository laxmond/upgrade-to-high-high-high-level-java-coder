## helm3查询、下载、安装 资源包



#### 1、查询资源包

添加完上面的 helm 仓库后，就可以愉快的查找你深爱的程序包（chart）了

```shell
[root@control-plane ~]# helm search repo nginx
NAME                   	CHART VERSION	APP VERSION	DESCRIPTION
stable/nginx-ingress   	0.9.5        	0.10.2     	An nginx Ingress controller that uses ConfigMap...
stable/nginx-lego      	0.3.1        	           	Chart for nginx-ingress-controller and kube-lego
stable/gcloud-endpoints	0.1.0        	           	Develop, deploy, protect and monitor your APIs ...
```

上述命令，是查询nginx的资源包



#### 2、下载资源包

使用命令`helm pull chart_name`下载

```shell
[root@control-plane te]# helm pull stable/nginx-ingress
[root@control-plane te]# ll
总用量 12
-rw-r--r-- 1 root root 10830 10月  9 02:11 nginx-ingress-0.9.5.tgz
```



#### 3、安装资源包

解压上面下载的资源包

```shell
[root@control-plane te]# tar mzxvf nginx-ingress-0.9.5.tgz
nginx-ingress/Chart.yaml
nginx-ingress/values.yaml
nginx-ingress/templates/NOTES.txt
nginx-ingress/templates/_helpers.tpl
nginx-ingress/templates/clusterrole.yaml
nginx-ingress/templates/clusterrolebinding.yaml
nginx-ingress/templates/controller-configmap.yaml
nginx-ingress/templates/controller-daemonset.yaml
nginx-ingress/templates/controller-deployment.yaml
nginx-ingress/templates/controller-hpa.yaml
nginx-ingress/templates/controller-metrics-service.yaml
nginx-ingress/templates/controller-poddisruptionbudget.yaml
nginx-ingress/templates/controller-service.yaml
nginx-ingress/templates/controller-stats-service.yaml
nginx-ingress/templates/default-backend-deployment.yaml
nginx-ingress/templates/default-backend-poddisruptionbudget.yaml
nginx-ingress/templates/default-backend-service.yaml
nginx-ingress/templates/headers-configmap.yaml
nginx-ingress/templates/role.yaml
nginx-ingress/templates/rolebinding.yaml
nginx-ingress/templates/serviceaccount.yaml
nginx-ingress/templates/tcp-configmap.yaml
nginx-ingress/templates/udp-configmap.yaml
nginx-ingress/.helmignore
nginx-ingress/README.md
[root@control-plane te]# ls
nginx-ingress  nginx-ingress-0.9.5.tgz
```



使用如下命令进行安装

```shell
helm install nginx-ingress --namespace tw nginx-ingress
```

第一个 nginx-ingress 是 release 名，tw是命名空间，第二个 nginx-ingress 是 chart 解压后的目录



如果安装过程中出现`Error: unable to build kubernetes objects from release manifest: [unable to recognize "": no matches for kind "PodDisruptionBudget" in version "policy/v1beta1", unable to recognize "": no matches for kind "Deployment" in version "extensions/v1beta1"]` 错误，大概率是k8s的版本不兼容，就需要挨个修改文件，修改成跟目前k8s版本兼容的语法！