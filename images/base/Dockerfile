FROM openjdk:8-jdk

MAINTAINER Luis David Barrios Alfonso (luisdavid.barrios@agsnasoft.com / cyberluisda@gmail.com)


ENV SPARK_VERSION 2.1.1
ENV HADOOP_VERSION 2.7
#ADD http://apache.rediris.es/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz /usr/lib
ADD http://mirrors.ocf.berkeley.edu/apache/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz /usr/lib
RUN cd /usr/lib && tar -zxvf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz > /dev/null && rm -f spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && cd - > /dev/null
RUN mv /usr/lib/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} /usr/lib/spark && rm -fr /usr/lib/spark/examples

#Add hadoop s3 support
RUN curl "https://search.maven.org/remotecontent?filepath=org/apache/hadoop/hadoop-aws/2.7.3/hadoop-aws-2.7.3.jar" -o /usr/lib/spark/jars/hadoop-aws-2.7.3.jar && curl "https://search.maven.org/remotecontent?filepath=com/amazonaws/aws-java-sdk/1.7.4/aws-java-sdk-1.7.4.jar" -o /usr/lib/spark/jars/aws-java-sdk-1.7.4.jar

ENV SPARK_HOME /usr/lib/spark
ENV PATH $PATH:/usr/lib/spark/bin

#install ivy
RUN apt-get update && apt-get install ivy && rm -rf /var/lib/apt/lists/*

EXPOSE 4040
VOLUME /var/lib/spark-extra /var/data/spark

WORKDIR /var/work
