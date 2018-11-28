# k8s-kong-konga-cluster
kong-api with cassandra and konga with galera mariadb as admin UI for kong  

1.
```
$ git clone [this repo](../)
$ cd k8s-kong-konga-cluster
```
2.
```
$ kubectl create -f 01-storageClass.yaml
```
3.
```
$ kubectl create -f 02-etcd-cluster.yaml
```
4.
```
$ kubectl create -f 03-cassandra.yaml
```
5.
```
$ kubectl create -f 04-galeraMariaDB.yaml
```
6.
```
$ kubectl create -f 05-kong_migration_cassandra.yaml
```
7.
```
$ kubectl create -f 06-kong_cassandra.yaml
```
8.
```
$ kubectl run konga-prepare --image pantsel/konga:next -- -c prepare -a mysql -u mysql://kong:kong@mariadb:3306/konga_database
```
9.
```
$ kubectl create -f 08-konga-galeraMariaDB
```
