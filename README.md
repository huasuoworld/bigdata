# bigdata


hbase-1.2.6
hadoop-2.7.5
zookeeper-3.3.6
apache-phoenix-4.13.1-HBase-1.2-bin
jdk1.8.0_151
spark-2.1.1-bin-hadoop2.7



Spark run on Kubernetes cluster

[http://spark.apache.org/docs/latest/running-on-kubernetes.html](http://spark.apache.org/docs/latest/running-on-kubernetes.html)



### RBAC

1.

```bash
 kubectl create serviceaccount spark
```

2.

```bash
$ kubectl create clusterrolebinding spark-role --clusterrole=edit --serviceaccount=spark-cluster:spark --namespace=spark-cluster
```



3.

bin/spark-submit --class com.huasuoworld.Grouping --master k8s://http://192.168.1.5:8080 --deploy-mode cluster --name spark-es-grouping --conf spark.kubernetes.namespace=spark-cluster --conf spark.executor.instances=1 --conf spark.kubernetes.container.image=docker.io/huasuoworld/spark:latest --conf spark.kubernetes.authenticate.driver.serviceAccountName=spark /opt/spark/examples/jars/spark-es-grouping.jar
