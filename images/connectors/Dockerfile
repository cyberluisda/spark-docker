FROM cyberluisda/spark:2.1.2

LABEL maintainer="Luis David Barrios Alfonso (cyberluisda@gmail.com)"


#add spark extra  libs
RUN mkdir -p /usr/lib/spark/third
ADD files/ivy.xml files/ivy-settings.xml /usr/lib/spark/third/
RUN java -jar /usr/share/java/ivy.jar -settings /usr/lib/spark/third/ivy-settings.xml -ivy /usr/lib/spark/third/ivy.xml -retrieve "/usr/lib/spark/third/[artifact].[ext]"

ENV ES_CONNECTOR_VERSION 6.1.3
# Elastic search connector now is extracted from zip
RUN curl \
    -sLo /tmp/elasticsearch-hadoop-${ES_CONNECTOR_VERSION}.zip \
    http://download.elastic.co/hadoop/elasticsearch-hadoop-${ES_CONNECTOR_VERSION}.zip \
  && unzip \
    /tmp/elasticsearch-hadoop-${ES_CONNECTOR_VERSION}.zip \
    -d /tmp \
  && cp \
    -v \
    /tmp/elasticsearch-hadoop-${ES_CONNECTOR_VERSION}/dist/elasticsearch-spark-20_2.11-${ES_CONNECTOR_VERSION}.jar \
    /usr/lib/spark/third/ \
  && rm -fr \
    /tmp/elasticsearch-hadoop-${ES_CONNECTOR_VERSION}/*

ADD files/spark-defaults.conf /usr/lib/spark/conf/
