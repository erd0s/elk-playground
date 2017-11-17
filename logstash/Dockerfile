FROM docker.elastic.co/logstash/logstash:6.0.0
RUN bin/logstash-plugin install logstash-filter-geoip
COPY pipeline /usr/share/logstash/pipeline
COPY logstash.yml /usr/share/logstash/config/logstash.yml