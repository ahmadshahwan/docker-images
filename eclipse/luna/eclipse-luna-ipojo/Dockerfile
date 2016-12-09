FROM ubuntu:14.04
MAINTAINER Fabio Rehm "fgrehm@gmail.com"

RUN sed 's/main$/main universe/' -i /etc/apt/sources.list && \
    apt-get update && apt-get install -y software-properties-common && \
    add-apt-repository ppa:webupd8team/java -y && \
    apt-get update && \
    echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections && \
    apt-get install -y oracle-java8-installer libxext-dev libxrender-dev libxtst-dev libgtk2.0-0 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/*

RUN cd /opt && \
    wget http://download.eclipse.org/technology/epp/downloads/release/luna/SR2/eclipse-rcp-luna-SR2-linux-gtk-x86_64.tar.gz && \
    tar -xzvf eclipse-rcp-luna-SR2-linux-gtk-x86_64.tar.gz && \
    rm eclipse-rcp-luna-SR2-linux-gtk-x86_64.tar.gz

RUN ./opt/eclipse/eclipse \
    -application org.eclipse.equinox.p2.director \
    -noSplash \
    -repository http://chameleon.ow2.org/eclipse/eclipse-ipojo-builder \
    -installIUs org.ow2.chameleon.eclipse.ipojo.m2e.feature.feature.group,org.ow2.chameleon.eclipse.ipojo.dependencies.feature.feature.group,org.ow2.chameleon.eclipse.ipojo.nature.feature.feature.group
