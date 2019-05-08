# k8s-elastic
利用K8S部署ELK服务

## 快速部署Elasticsearch

索引文件存放在`/data`目录下，以pvc挂载至容器内部`/usr/share/elasticsearch/data`目录，启动命令及es配置参数在ymal文件中进行配置。

```bash
kubectl apply -f es.yml
curl -s http://localhost:29200
```

## 快速部署Kibana

kibana配置文件在ymal文件中进行配置。

```bash
kubectl apply -f kibana.yml
curl -s http://localhost:25601
```

## 快速部署Gohangout

配置文件存放在`/data2`目录下，以pvc挂载至容器内部`/usr/share/gohangout`目录，启动命令在yaml文件中进行配置。

```bash
kubectl apply -f gohangout.yml
curl -s http://localhost:29200/_cat/indices|sort|grep gohangout-kafka-dnsmasq-2019-05-08
```

## 参考文档

- [在Kubernetes上部署Elasticsearch集群](https://blog.csdn.net/chenleiking/article/details/79453460)
- [在Kubernetes上部署Kibana和Logstash](https://blog.csdn.net/chenleiking/article/details/79466158)
