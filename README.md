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

1. 查看某index下的文档

```
curl --location --request GET 'localhost:9200/learn/_search' \
--header 'Content-Type: application/json' \
--data-raw '// 聚合
{
    "query": {
        "match_all": {}
    }
}
```

2. 在某index下创建文档(id随机)

```
curl --location --request POST 'localhost:9200/learn/_doc' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 1,
    "name": "",
    "age": 21
}'
```

3. 在某index下创建文档(id指定)

```
curl --location --request POST 'localhost:9200/learn/_doc/5' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 5,
    "name": "张飞",
    "age": 22
}'
```

4. 查看某index下的指定文档(指定id)

```
curl --location --request GET 'localhost:9200/learn/_doc/1'
```

5. 文档全局修改(指定id)

```
curl --location --request POST 'localhost:9200/learn/_doc/1' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name":"修改后的王武"
}'
```

6. 文档局部修改(指定id)

```
curl --location --request POST 'http://localhost:9200/learn/_doc/SmU_uIUB_sI_GoYmlaaW/_update' \
--header 'Content-Type: application/json' \
--data-raw '{
    "doc": {
        "name": "修改之后的张三"
    }
}'
```

7. 删除指定文档

```
curl --location --request DELETE 'localhost:9200/learn/_doc/1'
```

8. 获取批量文档

```
curl --location --request POST 'localhost:9200/_mget' \
--header 'Content-Type: application/json' \
--data-raw '{
    "docs": [{
        "_source": ["id"],
        "_index": "learn",
        "_type": "_doc",
        "_id":1
        },{
            "_index": "shopping",
            "_type": "_doc",
            "_id":1
        }
    ]
}'
```

9. 通过某字段获取批量文档

```
curl --location --request POST 'localhost:9200/learn/_mget' \
--header 'Content-Type: application/json' \
--data-raw '{
    "ids":[1, 2, 3, 4]
}'
```



### 三、映射

视频资料：

1. https://www.bilibili.com/video/BV1R4411C7Tf?p=15&spm_id_from=pageDriver&vd_source=d438475747553cd6444d27541dcaf56a
2。 https://www.cnblogs.com/chenqionghe/p/15153420.html#%E6%9C%89%E6%B2%A1%E6%9C%89sql%E7%94%9F%E6%88%90dsl%E7%9A%84%E5%B7%A5%E5%85%B7
