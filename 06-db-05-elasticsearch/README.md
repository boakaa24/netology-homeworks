1.
```
FROM centos:centos7

RUN yum -y install wget; yum clean all && \
        groupadd --gid 1000 elasticsearch && \
        adduser --uid 1000 --gid 1000 --home /usr/share/elasticsearch elasticsearch && \
        mkdir /var/lib/elasticsearch/ && \
        chown -R 1000:1000 /var/lib/elasticsearch/

USER 1000:1000

WORKDIR /usr/share/elasticsearch

ENV EL_VER=8.2.2

RUN wget -q http://192.168.1.168/elasticsearch-${EL_VER}-linux-x86_64.tar.gz && \
        tar -xzf elasticsearch-${EL_VER}-linux-x86_64.tar.gz && \
        cp -rp elasticsearch-${EL_VER}/* ./ && \
        rm -rf elasticsearch-${EL_VER}*

COPY ./elasticsearch.yml /usr/share/elasticsearch/config/

EXPOSE 9200

CMD ["bin/elasticsearch"]
```
```
https://hub.docker.com/repository/docker/boakaa24/elasticsearch
```

```
[elasticsearch@b14080a7d7c2 ~]$ curl --cacert /usr/share/elasticsearch/config/certs/http_ca.crt -u elastic https://localhost:9200
Enter host password for user 'elastic':
{
  "name" : "netology_test",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "0D5GRqBPSFGRbpWiUP-eHg",
  "version" : {
    "number" : "8.2.2",
    "build_flavor" : "default",
    "build_type" : "tar",
    "build_hash" : "9876968ef3c745186b94fdabd4483e01499224ef",
    "build_date" : "2022-05-25T15:47:06.259735307Z",
    "build_snapshot" : false,
    "lucene_version" : "9.1.0",
    "minimum_wire_compatibility_version" : "7.17.0",
    "minimum_index_compatibility_version" : "7.0.0"
  },
  "tagline" : "You Know, for Search"
  ```
2.
``[elasticsearch@b14080a7d7c2 ~]$ curl --cacert /usr/share/elasticsearch/config/certs/http_ca.crt -u elastic -X PUT https://localhost:9200/ind-1?pretty -H 'Content-Type: application/json' -d'{ "settings": { "index": { "number_of_shards": 1, "number_of_replicas": 0 }}}'
Enter host password for user 'elastic':
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "ind-1"
}
[elasticsearch@b14080a7d7c2 ~]$ curl --cacert /usr/share/elasticsearch/config/certs/http_ca.crt -u elastic -X PUT https://localhost:9200/ind-2?pretty -H 'Content-Type: application/json' -d'{ "settings": { "index": { "number_of_shards": 2, "number_of_replicas": 1 }}}'
Enter host password for user 'elastic':
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "ind-2"
}
[elasticsearch@b14080a7d7c2 ~]$ curl --cacert /usr/share/elasticsearch/config/certs/http_ca.crt -u elastic -X PUT https://localhost:9200/ind-3?pretty -H 'Content-Type: application/json' -d'{ "settings": { "index": { "number_of_shards": 4, "number_of_replicas": 2 }}}'
Enter host password for user 'elastic':
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "ind-3"
}
```
```
[elasticsearch@b14080a7d7c2 ~]$ curl --cacert /usr/share/elasticsearch/config/certs/http_ca.crt -u elastic https://localhost:9200/_cat/indices?v
Enter host password for user 'elastic':
health status index uuid                   pri rep docs.count docs.deleted store.size pri.store.size
yellow open   ind-2 zQqahdcNR8GcShl0221GBg   2   1          0            0       450b           450b
green  open   ind-1 BvZz2RAzSH2SeZAdrgj1vw   1   0          0            0       225b           225b
yellow open   ind-3 cjYATXsqRnanLFFE43DU_g   4   2          0            0       900b           900b
```
```
[elasticsearch@b14080a7d7c2 ~]$ curl --cacert /usr/share/elasticsearch/config/certs/http_ca.crt -u elastic https://localhost:9200/_cluster/health?pretty
Enter host password for user 'elastic':
{
  "cluster_name" : "elasticsearch",
  "status" : "yellow",
  "timed_out" : false,
  "number_of_nodes" : 1,
  "number_of_data_nodes" : 1,
  "active_primary_shards" : 9,
  "active_shards" : 9,
  "relocating_shards" : 0,
  "initializing_shards" : 0,
  "unassigned_shards" : 10,
  "delayed_unassigned_shards" : 0,
  "number_of_pending_tasks" : 0,
  "number_of_in_flight_fetch" : 0,
  "task_max_waiting_in_queue_millis" : 0,
  "active_shards_percent_as_number" : 47.368421052631575
}
```
Состояние yellow связано с тем, что есть unassigned шарды.
```
[elasticsearch@b14080a7d7c2 ~]$ curl --cacert /usr/share/elasticsearch/config/certs/http_ca.crt -u elastic -X DELETE https://localhost:9200/ind-1?pretty
Enter host password for user 'elastic':
{
  "acknowledged" : true
}
[elasticsearch@b14080a7d7c2 ~]$ curl --cacert /usr/share/elasticsearch/config/certs/http_ca.crt -u elastic -X DELETE https://localhost:9200/ind-2?pretty
Enter host password for user 'elastic':
{
  "acknowledged" : true
}
[elasticsearch@b14080a7d7c2 ~]$ curl --cacert /usr/share/elasticsearch/config/certs/http_ca.crt -u elastic -X DELETE https://localhost:9200/ind-3?pretty
Enter host password for user 'elastic':
{
  "acknowledged" : true
}
```
3.

