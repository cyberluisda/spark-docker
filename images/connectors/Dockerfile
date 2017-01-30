FROM cyberluisda/spark:1.6.3

MAINTAINER Luis David Barrios Alfonso (luisdavid.barrios@agsnasoft.com / cyberluisda@gmail.com)

#install ivy
RUN apt-get update && apt-get install ivy && rm -rf /var/lib/apt/lists/*

#add spark-js libs
RUN mkdir -p /usr/lib/spark/third
ADD files/ivy.xml files/ivy-settings.xml /usr/lib/spark/third/
RUN java -jar /usr/share/java/ivy.jar -settings /usr/lib/spark/third/ivy-settings.xml -ivy /usr/lib/spark/third/ivy.xml -retrieve "/usr/lib/spark/third/[artifact].[ext]"

ADD files/spark-defaults.conf /opt/spark/conf/

WORKDIR /var/data/spark
