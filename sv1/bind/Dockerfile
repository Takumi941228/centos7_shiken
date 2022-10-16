FROM centos:7

RUN yum install -y bind bind-utils
RUN yum -y install net-tools
RUN yum -y install firewalld

COPY named.conf /etc/
COPY j21.jyoho.com.exzone /var/named/
COPY j21.jyoho.com.inzone /var/named/
COPY 1.16.172.rzone /var/named/
COPY named.service /usr/lib/systemd/system/

RUN systemctl enable named
RUN systemctl enable firewalld

CMD ["/sbin/init"]
