FROM centos:7

RUN yum -y install bind bind-utils
RUN yum -y install net-tools
RUN yum -y install firewalld

COPY named.conf /etc/
COPY 1.168.192.rzone /var/named/
COPY named.service /usr/lib/systemd/system/

RUN systemctl enable named
RUN systemctl enable firewalld

CMD ["/sbin/init"]

