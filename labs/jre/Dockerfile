FROM       cisco/centos:7.1

ENV JAVA_VERSION 1.7.0
ENV JRE_HOME /usr/lib/jvm/jre

# Install jre
RUN yum -y install java-${JAVA_VERSION}-openjdk mysql && \
    yum clean all
