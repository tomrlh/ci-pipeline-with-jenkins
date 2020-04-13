FROM tomcat
MAINTAINER 'tomrlh'

RUN echo '<user username="admin" password="admin" roles="manager-gui,manager-script,manager-jmx,manager-status"/></tomcat-users>' >> /usr/local/tomcat/conf/tomcat-users.xml

RUN cd /usr/local/tomcat/webapps && \
    mkdir manager && \
    cd manager && \
    mkdir META-INF && \
    cd META-INF && \
    touch context.xml && \
    echo '<?xml version="1.0" encoding="UTF-8"?><Context privileged="true" antiResourceLocking="false" docBase="${catalina.home}/webapps/manager"><Valve className="org.apache.catalina.valves.RemoteAddrValve" allow="^.*$" /></Context>' >> context.xml

RUN cd /usr/local/tomcat/bin && \
    ./shutdown.sh && \
    ./startup.sh
