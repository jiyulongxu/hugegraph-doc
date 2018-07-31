### 1.4 IndexLabel

假设已经创建好了1.1.2中的 PropertyKeys 、1.2.2中的 VertexLabels 以及 1.3.2中的 EdgeLabels

#### 1.4.1 创建一个IndexLabel

##### Method

```
POST
```

##### Url

```
http://localhost:8080/graphs/hugegraph/schema/indexlabels
```

##### Request Body

```json
{
    "name": "personByCity",
    "base_type": "VERTEX_LABEL",
    "base_value": "person",
    "index_type": "SECONDARY",
    "fields": [
        "city"
    ]
}
```

##### Response Status

```json
201
```

##### Response Body

```json
{
    "id": 1,
    "base_type": "VERTEX_LABEL",
    "base_value": "person",
    "name": "personByCity",
    "fields": [
        "city"
    ],
    "index_type": "SECONDARY"
}
```

#### 1.4.2 获取所有的IndexLabel

##### Method

```
GET
```

##### Url

```
http://localhost:8080/graphs/hugegraph/schema/indexlabels
```

##### Response Status

```json
200
```

##### Response Body

```json
{
    "indexlabels": [
        {
            "id": 3,
            "base_type": "VERTEX_LABEL",
            "base_value": "software",
            "name": "softwareByPrice",
            "fields": [
                "price"
            ],
            "index_type": "RANGE"
        },
        {
            "id": 4,
            "base_type": "EDGE_LABEL",
            "base_value": "created",
            "name": "createdByDate",
            "fields": [
                "date"
            ],
            "index_type": "SECONDARY"
        },
        {
            "id": 1,
            "base_type": "VERTEX_LABEL",
            "base_value": "person",
            "name": "personByCity",
            "fields": [
                "city"
            ],
            "index_type": "SECONDARY"
        },
        {
            "id": 3,
            "base_type": "VERTEX_LABEL",
            "base_value": "person",
            "name": "personByAgeAndCity",
            "fields": [
                "age",
                "city"
            ],
            "index_type": "SECONDARY"
        }
    ]
}
```

#### 1.4.3 根据name获取IndexLabel

##### Method

```
GET
```

##### Url

```
http://localhost:8080/graphs/hugegraph/schema/indexlabels/personByCity
```

##### Response Status

```json
200
```

##### Response Body

```json
{
    "id": 1,
    "base_type": "VERTEX_LABEL",
    "base_value": "person",
    "name": "personByCity",
    "fields": [
        "city"
    ],
    "index_type": "SECONDARY"
}
```

#### 1.4.4 根据name删除IndexLabel

删除 IndexLabel 会导致删除相关的索引数据，会产生一个异步任务

##### Method

```
DELETE
```

##### Url

```
http://localhost:8080/graphs/hugegraph/schema/indexlabels/personByCity
```

##### Response Status

```json
202
```

##### Response Body

```json
{
    "task_id": 1
}
```

注：

> 可以通过`GET http://localhost:8080/graphs/hugegraph/tasks/1`（其中"1"是task_id）来查询异步任务的执行状态，更多[异步任务RESTful API](task.md)