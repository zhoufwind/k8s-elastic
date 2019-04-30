# k8s-elastic
利用K8S部署ELK服务

## 快速部署

```bash
kubectl apply -f es.yml
port=`kubectl -n ns-elastic get svc -owide|grep elasticsearch-service|awk '{print $5}'|awk -F : '{print $2}'|awk -F / '{print $1}'`
curl localhost:$port
```
## 参考文档

- [在Kubernetes上部署Elasticsearch集群](https://blog.csdn.net/chenleiking/article/details/79453460)
