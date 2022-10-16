FROM centos:7

RUN yum -y install squid
RUN yum -y install firewalld

COPY squid.conf /etc/squid/

RUN systemctl enable squid
RUN systemctl enable firewalld

CMD ["/sbin/init"]