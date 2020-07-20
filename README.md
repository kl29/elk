# elk

ELK activation (3 separate steps, all linked together locally, with Logstash using http-input plugin)
Overview: Logstash listens on port 5043, (input). Filters that input. Outputs to 9200 ElasticSearch.
Elasticsearch cluster takes the POST request. Sends it to Kibana dashboards. View your POSTs.

1) go in kibana folder, run 'elasticsearch' (port 9200, access at "localhost:9200")
    If 5601 has zombie process in use, do:

    lsof -i :5601
    kill -9 PID#

2) go in logstash folder, run 'logstash -f http-pipeline.conf'
    Should see 'Starting http input listener {address=>"0.0.0.0:5043", ... }
    Use POSTMAN to send POST data to 5043 (message: 'ok')

3) go in kibana folder, 'kibana', goto 'localhost:5601'

4) for Filebeat ES logs, go to filebeat folder, 
'filebeat setup' (this takes a few mins), 
'filebeat -e' (starts filebeat per the filebeat.yml config file)
for tips, see: http://localhost:5601/app/kibana#/home/tutorial/elasticsearchLogs

MISC: check Elasticsearch 9200 has indices:
http://localhost:9200/_cat/indices?v

