# k8s-kong-konga-cluster
kong-api with cassandra and konga with galera mariadb as admin UI for kong

1. Clone  
`$ git clone` [this repo](/../../)  
`$ cd k8s-kong-konga-cluster`  

2. Run yaml scripts  
```
$ kubectl create -f 01-storageClass.yaml
$ kubectl create -f 02-etcd-cluster.yaml
$ kubectl create -f 03-cassandra.yaml
$ kubectl create -f 04-galeraMariaDB.yaml
$ kubectl create -f 05-kong_migration_cassandra.yaml
$ kubectl create -f 06-kong_cassandra.yaml
$ kubectl run konga-prepare --image pantsel/konga:next -- -c prepare -a mysql -u mysql://kong:kong@mariadb:3306/konga_database
$ kubectl create -f 08-konga-galeraMariaDB
```
