# k8s-elastic
利用K8S部署ELK服务（v7.2.0）

## 部署Elasticsearch

`es-master`索引文件存放在`/var/lib/docker/data/es/master`目录下，`es-data`索引文件存放在`/var/lib/docker/data/es/data`目录下，以pvc挂载至容器内部`/usr/share/elasticsearch/data`目录，启动命令及es配置参数在YAML文件中进行配置。

```bash

# 创建物理文件夹
mkdir /var/lib/docker/data/es/master
mkdir /var/lib/docker/data/es/data

# 创建namespace
kubectl apply -f ns.yml

# 创建私有仓库权限
kubectl create secret docker-registry regcred-elastic --docker-server=dockerhub-pr.yeshj.com --docker-username=xxx --docker-password=xxx --docker-email=xxx -n ns-elastic

# 创建es服务
kubectl apply -f es-service.yml
kubectl apply -f es-master.yml
kubectl apply -f es-data.yml

# 验证es服务
curl -s http://localhost:29200
```

## 部署Kibana

kibana配置文件定义在YAML文件中。

```bash
# 创建kibana服务
kubectl apply -f kibana.yml

# 验证kibana服务
curl -s http://localhost:25601
```

## 部署Gohangout

gohangout配置文件定义在ConfigMap中。

```bash
# 创建gohangout服务
kubectl apply -f gohangout-dnsmasq-k8s.yml
```

## 部署Logstash

logstash配置文件定义在ConfigMap中。

```
# 创建logstash服务
kubectl apply -f logstash-named-k8s.yml
```

## 参考文档

- [在Kubernetes上部署Elasticsearch集群](https://blog.csdn.net/chenleiking/article/details/79453460)
- [在Kubernetes上部署Kibana和Logstash](https://blog.csdn.net/chenleiking/article/details/79466158)
- [Configuring Logstash for Dockeredit](https://www.elastic.co/guide/en/logstash/current/docker-config.html)
- [通过环境变量将Pod信息呈现给容器](https://kubernetes.io/zh/docs/tasks/inject-data-application/environment-variable-expose-pod-information/)
- [Master not discovered yet, this node has not previously joined a bootstrapped (v7+) cluster](https://discuss.elastic.co/t/master-not-discovered-yet-this-node-has-not-previously-joined-a-bootstrapped-v7-cluster/176304)
- [elasticsearch-kubed](https://github.com/jswidler/elasticsearch-kubed)
