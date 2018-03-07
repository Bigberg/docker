FROM centos
MAINTAINER bigberg

ADD jdk-8u121-linux-x64.tar.gz /usr/local
ENV JAVA_HOME /usr/local/jdk1.8.0_121
ADD apache-tomcat-8.5.12.tar.gz /usr/local
COPY server.xml /usr/local/apache-tomcat-8.5.12/conf/server.xml

EXPOSE 8080
ENTRYPOINT ["/usr/local/apache-tomcat-8.5.12/bin/catalina.sh", "run"]
