# k8s-elastic
利用K8S部署ELK服务（v6.5.1）

## 快速部署Elasticsearch

索引文件存放在`/var/lib/docker/data/es`目录下，以pvc挂载至容器内部`/usr/share/elasticsearch/data`目录，启动命令及es配置参数在YAML文件中进行配置。

```bash
# 创建namespace
kubectl apply -f ns.yml

# 创建es服务
kubectl apply -f es.yml

# 验证es服务
curl -s http://localhost:29200
```

## 快速部署Kibana

kibana配置文件在YAML文件中进行配置：

```bash
# 创建kibana服务
kubectl apply -f kibana.yml

# 验证kibana服务
curl -s http://localhost:25601
```

## 快速部署Gohangout

gohangout配置文件定义在ConfigMap配置中进行配置：

```bash
# 创建gohangout服务
kubectl apply -f gohangout-dnsmasq-k8s.yml

# 查询创建的索引
curl -s http://localhost:29200/_cat/indices|sort|grep gohangout-kafka-dnsmasq-2019-05-08
```

## 参考文档

- [在Kubernetes上部署Elasticsearch集群](https://blog.csdn.net/chenleiking/article/details/79453460)
- [在Kubernetes上部署Kibana和Logstash](https://blog.csdn.net/chenleiking/article/details/79466158)
