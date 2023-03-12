# ElasticSearch-Notes
ES学习笔记

### 一、索引

1. 查看索引信息

```
curl --location --request GET 'localhost:9200/_cat/indices?v'
```

2. 创建索引

```
curl --location --request PUT 'localhost:9200/learn'
```

3. 查看某个索引

```
curl --location --request GET 'localhost:9200/learn'
```

4. 删除某个索引

```
curl --location --request DELETE 'localhost:9200/learn'
```

5. 关闭某个索引

```
curl --location --request POST 'localhost:9200/learn/_close'
```

6. 打开某个索引

```
curl --location --request POST 'localhost:9200/learn/_open'
```

7. 关闭所有索引

```
curl --location --request POST 'localhost:9200/_all/_close'
```

8. 索引复制

```
curl --location --request POST 'localhost:9200/_reindex' \
--header 'Content-Type: application/json' \
--data-raw '{
    "source":{"index":"learn"},
    "dest": {"index":"learn_dest"}
}'
```

9. 索引别名



### 二、文档

### 三、映射

视频资料：

1. https://www.bilibili.com/video/BV1R4411C7Tf?p=15&spm_id_from=pageDriver&vd_source=d438475747553cd6444d27541dcaf56a
2。 https://www.cnblogs.com/chenqionghe/p/15153420.html#%E6%9C%89%E6%B2%A1%E6%9C%89sql%E7%94%9F%E6%88%90dsl%E7%9A%84%E5%B7%A5%E5%85%B7
