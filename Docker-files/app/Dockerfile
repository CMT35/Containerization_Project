# Multi-stage dockerfile 
# Use openjdk as your primary build image and install maven which will be used to build the artifact 
FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone 
RUN cd vprofile-project && git checkout docker && mvn install

# Copy generated artifact into image we want to build
FROM tomcat:9-jre11
LABEL "Project"="Containerization_Project"
LABEL "Author"="CMT35"
# Remove the default tomcat application/artifact (from offical tomcat documentation)
RUN rm-rf /usr/local/tomcat/webapps/* 
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
# Default tomcat server
CMD ["catalina.sh", "run"]