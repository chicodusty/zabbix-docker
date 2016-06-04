FROM centos:centos7

LABEL io.k8s.description="Zabbix Monitoring UI for Openshift" \
      io.k8s.display-name="Zabbix 3.0" \
      io.openshift.expose-services="80:zabbix-web" \
      io.openshift.tags="zabbix-web"

# Install Zabbix release packages.
RUN yum install -y http://repo.zabbix.com/zabbix/3.0/rhel/7/x86_64/zabbix-release-3.0-1.el7.noarch.rpm

RUN yum install -y zabbix-web       \
                   zabbix-web-mysql \

# Zabbix Conf Files
ADD ./zabbix_web_files/zabbix.ini 				    /etc/php.d/zabbix.ini
ADD ./zabbix_web_files/httpd_zabbix.conf  		/etc/httpd/conf.d/zabbix.conf
ADD ./zabbix_web_files/zabbix.conf.php    		/etc/zabbix/web/zabbix.conf.php

# Expose port 80 for http
EXPOSE 80

CMD ["/usr/sbin/apachectl", "-DFOREGROUND"]
