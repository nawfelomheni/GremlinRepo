FROM ubuntu:14.04

RUN apt-get update && apt-get -y upgrade
RUN apt-get install python-pip python-dev -y
RUN pip install flask flask_json json2html simplejson
RUN apt-get install -y python-gevent

RUN apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor

ADD login.defs /etc/login.defs

RUN mkdir -p /opt/microservices
ADD start_all.sh /opt/microservices/start_all.sh
RUN chmod a+x /opt/microservices/start_all.sh

ADD templates /opt/microservices/templates
ADD details-supervisor.conf /etc/supervisor/conf.d/details.conf
ADD details.py /opt/microservices/details.py

EXPOSE 9080
WORKDIR /opt/microservices

#ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

CMD ["/opt/microservices/start_all.sh"]
