FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/sunilkapare/dockerproject2.git
RUN cd dockerproject2 && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Dockerproject"
LABEL "Author"="Imran"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE dockerproject2/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh","run"]

