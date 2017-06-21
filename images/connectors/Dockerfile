FROM cyberluisda/spark:2.1.1

MAINTAINER Luis David Barrios Alfonso (cyberluisda@gmail.com)

#add spark extra  libs
RUN mkdir -p /usr/lib/spark/third
ADD files/ivy.xml files/ivy-settings.xml /usr/lib/spark/third/
RUN java -jar /usr/share/java/ivy.jar -settings /usr/lib/spark/third/ivy-settings.xml -ivy /usr/lib/spark/third/ivy.xml -retrieve "/usr/lib/spark/third/[artifact].[ext]"

ADD files/spark-defaults.conf /usr/lib/spark/conf/
