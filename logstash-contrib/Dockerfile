# This is basically logstash with the contributrion modules installed

FROM logstash:1.4.2
MAINTAINER Anthony Oliver <anthony@sightmachine.com>

WORKDIR /opt/logstash
RUN wget http://download.elasticsearch.org/logstash/logstash/logstash-contrib-1.4.2.tar.gz
RUN tar zxvf logstash-contrib-1.4.2.tar.gz --strip 1