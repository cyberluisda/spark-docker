FROM openjdk:8-jdk

MAINTAINER Luis David Barrios Alfonso (luisdavid.barrios@agsnasoft.com / cyberluisda@gmail.com)


ENV SPARK_VERSION 1.6.3
ENV HADOOP_VERSION 2.6
ADD http://apache.rediris.es/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz /usr/lib
RUN cd /usr/lib && tar -zxvf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz > /dev/null && rm -f spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && cd - > /dev/null
RUN mv /usr/lib/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} /usr/lib/spark && rm -fr /usr/lib/spark/examples

ENV SPARK_HOME /usr/lib/spark
ENV PATH $PATH:/usr/lib/spark/bin

EXPOSE 4040
VOLUME /var/lib/spark-extra /var/data/spark

WORKDIR /var/data/spark
