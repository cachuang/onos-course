FROM ubuntu:16.04

# Update apt
RUN apt-get update 

# Install sudo
RUN apt-get install sudo -y

# Install ssh tool
RUN apt-get install openssh-server -y

# Install Java 8
RUN apt-get install software-properties-common -y
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
RUN add-apt-repository ppa:webupd8team/java -y
RUN apt-get update 
RUN apt-get install oracle-java8-installer -y
RUN rm -rf /var/lib/apt/lists/* 
RUN rm -rf /var/cache/oracle-jdk8-installer

# Set JAVA_HOME 
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

# Add user
RUN useradd -ms /bin/bash sdn
RUN echo 'sdn:sdn' | chpasswd
RUN echo "sdn ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# Start ssh server
ENTRYPOINT service ssh start && bash
