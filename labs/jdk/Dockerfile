FROM       cisco/centos:7.1

ENV JAVA_VERSION 1.7.0
ENV JDK_HOME /usr/lib/jvm/java-1.7.0-openjdk

# Install jdk
RUN yum -y install java-${JAVA_VERSION}-openjdk java-${JAVA_VERSION}-openjdk-devel && \
    yum clean all
