# docker pull docker.elastic.co/kibana/kibana:7.1.0
FROM docker.elastic.co/kibana/kibana:7.1.0

ADD config/ /usr/share/kibana/config/

EXPOSE 5601 

USER root

RUN yum install telnet curl wget -y 

USER kibana


