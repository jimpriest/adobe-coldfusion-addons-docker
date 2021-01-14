FROM eaps-docker-coldfusion.bintray.io/cf/coldfusion:latest-2018

COPY wwwroot/myconfig.json /app/

RUN apt-get update \ 
    && DEBIAN_FRONTEND=noninteractive apt-get --no-install-recommends install -y \
       curl \
       wget \
       unzip \
       gnupg \
       ca-certificates \
       apt-transport-https \
       openjdk-8-jdk \
    && curl -fsSl https://downloads.ortussolutions.com/debs/gpg | apt-key add - \
    && echo "deb http://downloads.ortussolutions.com/debs/noarch /" | tee -a /etc/apt/sources.list.d/commandbox.list \
    && apt-get update \ 
    && apt-get --no-install-recommends install -y commandbox \
    && apt-get clean \
    && rm -rf /tmp/* \
    && rm -rf /var/lib/apt/lists/* \
		# Fix certificate issues  (?)
		&& apt-get update \
		&& apt-get install ca-certificates-java \
		&& apt-get clean \
		&& update-ca-certificates -f

# Setup JAVA_HOME -- useful for docker commandline
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64/
RUN export JAVA_HOME

# setup cfconfig and apply settings
RUN /usr/local/bin/box install commandbox-cfconfig
RUN /usr/local/bin/box cfconfig import from=/app/myconfig.json to=/opt/coldfusion/cfusion/ toFormat=adobe@2018 

# update jvm settings
ADD jvm/jvm.config /opt/coldfusion/cfusion/bin/jvm.config