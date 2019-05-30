# k8s-elastic
利用K8S部署ELK服务（v6.5.1）

## 部署Elasticsearch

索引文件存放在`/var/lib/docker/data/es`目录下，以pvc挂载至容器内部`/usr/share/elasticsearch/data`目录，启动命令及es配置参数在YAML文件中进行配置。

```bash
# 创建namespace
kubectl apply -f ns.yml

# 创建es服务
kubectl apply -f es.yml

# 验证es服务
curl -s http://localhost:29200
```

## 部署Kibana

kibana配置文件定义在YAML文件中：

```bash
# 创建kibana服务
kubectl apply -f kibana.yml

# 验证kibana服务
curl -s http://localhost:25601
```

## 部署Gohangout

gohangout配置文件定义在ConfigMap中：

```bash
# 创建gohangout服务
kubectl apply -f gohangout-dnsmasq-k8s.yml
```

## 部署Logstash

logstash配置文件定义在ConfigMap中：

```
# 创建logstash服务
kubectl apply -f logstash-named-k8s.yml
```

## 参考文档

- [在Kubernetes上部署Elasticsearch集群](https://blog.csdn.net/chenleiking/article/details/79453460)
- [在Kubernetes上部署Kibana和Logstash](https://blog.csdn.net/chenleiking/article/details/79466158)
- [Configuring Logstash for Dockeredit](https://www.elastic.co/guide/en/logstash/current/docker-config.html)
