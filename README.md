# Elk Playground
Simple docker-compose environment for playing around with logstash filters and seeing them in kibana.

## Usage
* Everything is ready to go, just run `docker-compose build && docker-compose up`.
* Filebeat watches the logs in `./filebeat/logs` (config defined in `./filebeat/prospectors`)
* Lines added to the logs get sent to logstash
* Logstash applys the filters in `./logstash/pipeline` and sends them to elasticsearch
* Use kibana to see what's in logstash (http://localhost:5601)

## Notes
* `./logstash/pipeline` is mounted into the logstash container, any changes will cause logstash to reload config automatically.
* In the filebeat container, any changes to `./filebeat/prospectors/*` or `./filebeat/filebeat.yml` will require the filebeat container to be rebuilt and restarted `docker-compose build filebeat && docker-compose up -d filebeat`.
* The logs directory `./filebeat/logs` is mounted into the running filebeat container, so anything you add to this directory on the host will show up inside the container (and hence be sent to logstash from filebeat).

## Environment
* Access kibana at http://localhost:5601
* Logstash listens on 5044 and that port is exposed to the host if you need it.
* Elasticsearch listens on 9200 and is also exposed to the host.