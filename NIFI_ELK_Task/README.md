
# NIFI + ELK Task 

Display in a map the emergency calls from the following API using NIFI and ELK:

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

Once the data is in elasticsearch, in order to deal with to have the variable "location" as a geo_point variable the following reindex is done:




