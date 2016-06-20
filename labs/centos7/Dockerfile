
FROM       centos:centos7.1.1503

ENV TZ "Asia/Shanghai"
ENV TERM xterm

# Proxy Settings
ENV http_proxy=http://proxy-wsa.esl.cisco.com:80 \
    https_proxy=http://proxy-wsa.esl.cisco.com:80 \
    ftp_proxy=http://proxy-wsa.esl.cisco.com:80 \
    git_proxy=http://proxy-wsa.esl.cisco.com:80 \
    socks_server=http://proxy-wsa.esl.cisco.com:1080 \
    no_proxy="localhost,.localdomain,.cisco.com,.tandberg.com,10.74.20.158,10.74.20.154"

ADD cisco-mirror.repo /etc/yum.repos.d/CentOS-Base.repo
ADD cisco-epel.repo /etc/yum.repos.d/epel.repo

RUN yum install -y curl wget tar bzip2 unzip vim-enhanced passwd sudo yum-utils hostname net-tools rsync man && \
    yum install -y gcc gcc-c++ git make automake cmake patch logrotate python-devel libpng-devel libjpeg-devel && \
    yum install -y --enablerepo=epel pwgen python-pip && \
    yum clean all

RUN pip install supervisor
ADD supervisord.conf /etc/supervisord.conf

RUN mkdir -p /etc/supervisor.conf.d && \
    mkdir -p /var/log/supervisor

EXPOSE 22

ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]
