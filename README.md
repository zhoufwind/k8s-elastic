# k8s-elastic
利用K8S部署ELK服务

## 快速部署Elasticsearch

```bash
kubectl apply -f es.yml
curl -s http://localhost:29200
```

## 快速部署Kibana

```bash
kubectl apply -f kibana.yml
curl -s http://localhost:25601
```

## 参考文档

- [在Kubernetes上部署Elasticsearch集群](https://blog.csdn.net/chenleiking/article/details/79453460)
- [在Kubernetes上部署Kibana和Logstash](https://blog.csdn.net/chenleiking/article/details/79466158)
