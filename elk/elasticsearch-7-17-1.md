# ElasticSearch (7.17.1)

## ElasticSearch Useful commands

### Basic commands

| command                                       | description                                                         |
|-----------------------------------------------|---------------------------------------------------------------------|
| `GET /`                                       | Get Instance Information                                            |
| `GET /_stats`                                 | Get Statistics                                                      |
| `GET /_nodes`                                 | Get Nodes                                                           |
| `GET /_cat/indices`                           | Get Indices                                                         |

### Example commands

The following examples refer to a 'movie' index that can be replaced with your specific index.

| command                                       | description                                                         |
|-----------------------------------------------|---------------------------------------------------------------------|
| `POST /movies/_doc {...}`                     | Add a single document with random id                                |
| `PUT /movies/_doc/1 {...}`                    | Add a single document with id equals to 1                           |
| `PUT movies/_bulk { "create": { } } \n {...}` | Add multiple documents                                              |
| `POST /movies/_update/1 {"doc":{...}}`        | Update the document with id equals to 1                             |
| `GET /movies/_search [{...}]`                 | Search documents in an index (optional json)                        |
| `GET /movies/_doc/1`                          | Get the document in 'movies' index with id equals to 1              |
| `GET /movies`                                 | Get all informations of the 'movies' index                          |
| `GET /movies/_mapping`                        | Get the mapping of the 'movies' index                               |
| `DELETE /movies/_doc/1`                       | Delete a document with id equals to 1                               |
| `DELETE /movies`                              | Delete an index (with all documents inside)                         |

## Search Query Examples

### Search Query 'match_all'

```kibana
GET /movies/_search
{
  "query": {
    "match_all": {}
  }
}
```

### Search Query 'query_string'

```kibana
GET /movies/_search
{
  "query": {
    "query_string": {
      "default_field": "FIELD",
      "query": "this AND that OR thus"
    }
  }
}
```

```kibana
GET /movies/_search
{
  "query": {
    "query_string": {
      "query": "ford",
      "fields": ["title", "director^10"]
    }
  }
}
```

### Search Query 'filtered'

```kibana
GET /movies/_search
{
  "query": {
    "query_string": {
      "query": "ford",
      "fields": ["title", "director^10"]
    }
  }
}
```
