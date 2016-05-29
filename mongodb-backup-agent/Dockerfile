FROM centos:centos7
MAINTAINER Mikkel Christiansen <mikkel@rheosystems.com>

RUN yum install logrotate -y && yum clean all

ENV MMS_VERSION 4.3.0.384-1
RUN curl -sSL https://mms.mongodb.com/download/agent/backup/mongodb-mms-backup-agent-${MMS_VERSION}.x86_64.rhel7.rpm -o mms.rpm \
     && rpm -U mms.rpm \
     && rm mms.rpm

COPY entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]

USER mongodb-mms-agent
CMD ["mongodb-mms-backup-agent", "-c", "/etc/mongodb-mms/backup-agent.config"]
