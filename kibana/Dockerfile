FROM elasticsearch:1.5
MAINTAINER Anthony Oliver <anthony@sightmachine.com>

WORKDIR /opt/
RUN mkdir -p /opt/kibana
RUN wget https://download.elasticsearch.org/kibana/kibana/kibana-4.0.1-linux-x64.tar.gz
RUN tar zxvf kibana-4.0.1-linux-x64.tar.gz -C kibana --strip-components 1
WORKDIR /opt/kibana/
RUN sed -i 's,elasticsearch_url: "http://localhost:9200",elasticsearch_url: "http://elasticsearch:9200",g' config/kibana.yml
EXPOSE 5601
CMD bin/kibana