FROM openjdk:8-jdk

MAINTAINER Luis David Barrios Alfonso (luisdavid.barrios@agsnasoft.com / cyberluisda@gmail.com)


ENV SPARK_VERSION 2.1.0
ENV HADOOP_VERSION 2.7
ADD http://apache.rediris.es/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz /usr/lib
RUN cd /usr/lib && tar -zxvf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz > /dev/null && rm -f spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && cd - > /dev/null
RUN mv /usr/lib/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} /usr/lib/spark && rm -fr /usr/lib/spark/examples

ENV SPARK_HOME /usr/lib/spark
ENV PATH $PATH:/usr/lib/spark/bin

EXPOSE 4040
VOLUME /var/lib/spark-extra /var/data/spark

#install ivy
RUN apt-get update && apt-get install ivy && rm -rf /var/lib/apt/lists/*

#add spark-js libs
RUN mkdir -p /usr/lib/spark/third
ADD files/ivy.xml files/ivy-settings.xml /usr/lib/spark/third/
RUN java -jar /usr/share/java/ivy.jar -settings /usr/lib/spark/third/ivy-settings.xml -ivy /usr/lib/spark/third/ivy.xml -retrieve "/usr/lib/spark/third/[artifact].[ext]"

ADD files/spark-defaults.conf /opt/spark/conf/

WORKDIR /var/data/spark
