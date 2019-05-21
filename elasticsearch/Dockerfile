FROM docker.elastic.co/elasticsearch/elasticsearch:7.1.0

WORKDIR /usr/share/elasticsearch

RUN mv -f config/elasticsearch.yml config/elasticsearch.yml.orig

ADD config/ /usr/share/elasticsearch/config/

USER root
RUN chown elasticsearch:elasticsearch config/elasticsearch.yml && \
    yum install telnet curl wget -y 

EXPOSE 9200 9300

USER elasticsearch
RUN bin/elasticsearch-plugin install --batch discovery-ec2 && \
    bin/elasticsearch-plugin install --batch repository-s3 && \
#    bin/elasticsearch-plugin install --batch x-pack && \
    sed -e '/^-Xm/s/^/#/g' -i /usr/share/elasticsearch/config/jvm.options