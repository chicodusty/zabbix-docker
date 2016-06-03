FROM centos:centos7

LABEL io.k8s.description="Zabbix Monitoring Agent for Openshift" \
      io.k8s.display-name="Zabbix 3.0" \
      io.openshift.expose-services="10050:zabbix-agent" \
      io.openshift.tags="zabbix-agent"

ENV ZABBIX_SERVER=127.0.0.1 \
    HOSTNAME=zabbix.agent

# Install Zabbix release packages.
RUN yum install -y http://repo.zabbix.com/zabbix/3.0/rhel/7/x86_64/zabbix-release-3.0-1.el7.noarch.rpm

RUN yum install -y zabbix-agent

# RUN chown -R zabbix:zabbix /etc/zabbix/

USER zabbix

EXPOSE 10050

ENTRYPOINT ["/usr/sbin/zabbix_agentd","-f","-c","/etc/zabbix/zabbix_agentd.conf"]
