FROM amazonlinux:latest
MAINTAINER Ahmet Atalay

USER root

ENV	LANG en_US.UTF-8
ENV	LC_ALL en_US.UTF-8

#------ Install Following Linux Packages  ------
RUN yum install -y curl; yum install -y openssh; yum install -y vim; yum upgrade -y; yum update -y; yum install -y zip; yum install -y unzip; yum install -y which; yum install sudo; yum install -y findutils.x86_64; yum install -y git; yum clean all

#------ Install Java ------
ENV JDK_VERSION 8u92
ENV JDK_BUILD_VERSION b14
RUN curl -LO "http://download.oracle.com/otn-pub/java/jdk/$JDK_VERSION-$JDK_BUILD_VERSION/jdk-$JDK_VERSION-linux-x64.rpm" -H 'Cookie: oraclelicense=accept-securebackup-cookie' && rpm -i jdk-$JDK_VERSION-linux-x64.rpm; rm -f jdk-$JDK_VERSION-linux-x64.rpm; yum clean all
ENV JAVA_HOME /usr/java/default
ENV PATH $PATH:$JAVA_HOME/bin

#------ Install Node.js ------
RUN curl --silent --location https://rpm.nodesource.com/setup_6.x | bash -
RUN yum install -y nodejs; yum install -y gcc-c++ make

#------ Create Hubot user ------
ENV HOME /home/hubot
RUN useradd hubot -m
WORKDIR /home/hubot
