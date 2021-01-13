
# NIFI + ELK Task 

Display in a map the crimes registered from the following API using NIFI and ELK:

https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9

### Docker-compose file 

The docker infrastructure used is: 

| NIFI | 8877 | http://localhost:8877 |
|:----:|------|------------------------|

| Elasticsearch | 9200 | http://localhost:9200 |
|:-------------:|------|-----------------------|

| Kibana | 5601 | http://localhost:5601 |
|:----:|------|------------------------|


### NIFI Ingestion 

The flow used in NIFI: 

![alt text](https://github.com/Rosalln/MDA/blob/master/NIFI_ELK_Task/Img/Nifi_flow.png)

The NIFI template is available in MDA/NIFI_ELK_Task/Tarea2.xml

### KIBANA

Steps to create the dashboard once the data is in elasticsearch:

1. Create a new index with the desired geo_point property: 

```
PUT delitos_reindex  
{  
  "mappings": {  
      "properties": {  
        "location": {  
          "type": "geo_point"  
        }  
      }  
    }  
  }
 ```
2. Use reindex to copy the content to the new index:
 
 ```
 POST _reindex
{
  "source": {
    "index": "delitos"
  },
  "dest": {
    "index": "delitos_reindex"
  },
  "script": {
    "source": "ctx._source.location = ['lat': ctx._source.latitude, 'lon': ctx._source.longitude]; "
  }
}
```
3. Create an index pattern from the new index (delitos_reindex). 

4. Create a new visualization: Coordinate Map 

#### Dashboard

![alt text](https://github.com/Rosalln/MDA/blob/master/NIFI_ELK_Task/Dashboard.png)







 
  

  
 



