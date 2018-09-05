FROM xqual/xstudio-debian-java8:v3.3
MAINTAINER Jean Marin <jean@xqual.com>
	

# get wget  and unzip 
RUN apt-get update && \
	apt-get -y install wget && \
	apt-get -y install unzip
	
# Download XStudio , unzip and untar then install
RUN mkdir -p /usr/share/xqual && chdir /usr/share/xqual
RUN wget http://xstudio.alwaysdata.net/support/releases/3.3sp3/xstudio_v3_3sp3_linux.tar.zip
RUN unzip xstudio_v3_3sp3_linux.tar.zip -d /usr/share/xqual
RUN rm -f /usr/share/xqual/xstudio_v3_3sp3_linux.tar.zip 
RUN mv /usr/share/xqual/xstudio_v3_3sp3_linux.tar /usr/share/xqual/xstudio.tar
RUN tar -xvf /usr/share/xqual/xstudio.tar -C /usr/share/xqual
RUN rm -f /usr/share/xqual/xstudio.tar

#Copy Modified Xagent.sh to relocate in /usr/share/xqual
COPY xagent.sh /usr/share/xqual/xstudio/xagent.sh
# A better way would be to adapt the path to have /usr/share/xqual ?

RUN ln -sf /usr/share/xqual/xstudio/xagent.sh /usr/bin/xagent

# here we force this container to start an xagent - this may not be the desired need at the end 
CMD /usr/share/xqual/xstudio/xagent.sh --alias jules --poolDelay 60 --headless true --login admin:password --forceIpv4 true
	