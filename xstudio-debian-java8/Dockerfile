FROM debian:stable-slim
MAINTAINER Samuel Debruyn <s@muel.be>

ENV DEBIAN_FRONTEND noninteractive



# setup workdir
RUN mkdir -p /root/work/
WORKDIR /root/work/

# install apt-utils for debconf
RUN apt-get -y update && \
	apt-get -y install --no-install-recommends apt-utils

# install gnupg utils
RUN apt-get -y update && \
	apt-get install -y gnupg	
	
# install java 8for debian 	
RUN echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main" | tee /etc/apt/sources.list.d/webupd8team-java.list && \
	echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main" | tee -a /etc/apt/sources.list.d/webupd8team-java.list && \
	apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EEA14886 && \
	apt-get update -y 	
	
# accept oracle licence 	
RUN	echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
	echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections
	
# purge  and install java 8	
RUN mkdir -p /usr/share/man/man1 && \
	apt-get install -f && \
    apt-get purge oracle-java8-installer && \
	apt-get install oracle-java8-installer -y && \
	apt-get install oracle-java8-set-default && \
    apt-get clean autoclean && \
    apt-get autoremove -y && \
    rm -rf /var/cache/oracle* /var/log/* && \
    rm -rf /usr/lib/jvm/java-8-oracle/man /usr/lib/jvm/java-8-oracle/src.zip /usr/lib/jvm/java-8-oracle/javafx-src.zip /tmp/*
	
# slim down image
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/man/?? /usr/share/man/??_*


