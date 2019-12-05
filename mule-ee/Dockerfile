# Dockerizing Mule EE
# Version:  0.1
# Based on:  dockerfile/java (Trusted Java from http://java.com)

FROM                    openjdk:latest
#FROM                    garthk/unzip:latest
MAINTAINER              Conrad Pöpke <conrad@poepke.info>

# MuleEE installation:

# This line can reference either a web url (ADD), network share or local file (COPY)
ADD https://repository.mulesoft.org/nexus/content/repositories/releases/org/mule/distributions/mule-standalone/4.2.1/mule-standalone-4.2.1.zip /opt/

#ADD https://www.dropbox.com/s/zw39f9gc6rb0565/mule-ee.tar.gz?dl=0 /opt/

WORKDIR                 /opt
#RUN                     tar -xzvf /opt/mule-ee.tar.gz
RUN                     unzip /opt/mule-standalone-4.2.1.zip
RUN                     rm /opt/mule-standalone-4.2.1.zip
#RUN                     rm /opt/mule-ee.tar.gz
RUN                     ln -s /opt/mule-ee /opt/mule

# Configure external access:

# Mule remote debugger
EXPOSE  5000

# Mule JMX port (must match Mule config file)
EXPOSE  1098

# Mule MMC agent port
EXPOSE  7777

# Environment and execution:

ENV             MULE_BASE /opt/mule
WORKDIR         /opt/mule-ee-4.2.1

CMD             /opt/mule/bin/mule
