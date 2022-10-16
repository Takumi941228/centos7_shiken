FROM centos:7

RUN yum -y install epel-release
RUN yum -y install httpd mod_pearl
RUN yum -y install firewalld

ADD index.html /var/www/html/

RUN systemctl enable httpd
RUN systemctl enable firewalld

CMD ["/sbin/init"]