FROM centos:centos7
RUN curl --silent --location https://rpm.nodesource.com/setup_8.x | bash -
RUN curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
RUN yum -y update
RUN ACCEPT_EULA=Y yum -y install postgresql-libs msodbcsql17 unixODBC-devel zopfli nodejs
RUN yum clean all && rm -rf /var/cache/yum

RUN curl -sSL https://get.haskellstack.org/ | sh
RUN stack install hasql odbc
