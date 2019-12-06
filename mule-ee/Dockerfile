# Dockerizing Mule EE
# Version:  0.1
# Based on:  dockerfile/java (Trusted Java from http://java.com)

FROM                    openjdk:latest
#FROM                    garthk/unzip:latest
MAINTAINER              Conrad Pöpke <conrad@poepke.info>

# MuleEE installation:

# This line can reference either a web url (ADD), network share or local file (COPY)
#ADD https://repository.mulesoft.org/nexus/content/repositories/releases/org/mule/distributions/mule-standalone/4.2.1/mule-standalone-4.2.1.zip /opt/

ADD https://repository.mulesoft.org/nexus/content/repositories/releases/org/mule/distributions/mule-standalone/4.1.1/mule-standalone-4.1.1.tar.gz /opt/

WORKDIR                 /opt
RUN                     tar -xzvf /opt/mule-standalone-4.1.1.tar.gz
RUN                     echo "6b5c3ae9c87f95b00f0c1aff300ca70c550f1952 /opt/mule-standalone-4.1.1.tar.gz" | sha1sum -c
RUN                    rm /opt/mule-standalone-4.1.1.tar.gz
#RUN                    unzip /opt/mule-standalone-4.2.1.zip
#RUN                    rm /opt/mule-standalone-4.2.1.zip
RUN                     ln -s /opt/mule-standalone-4.1.1 /opt/mule

# Configure external access:

# Mule remote debugger
EXPOSE  5000

# Mule JMX port (must match Mule config file)
EXPOSE  1098

# Mule MMC agent port
EXPOSE  7777

# Environment and execution:

ENV             MULE_BASE /opt/mule
WORKDIR         /opt/mule-standalone-4.1.1

CMD             /opt/mule/bin/mule
