# Multi-stage dockerfile 
# Stage 1: Use openjdk as the primary build image and install maven to build the artifact 
FROM openjdk:11 AS BUILD_IMAGE
RUN apt-get update && apt-get install maven -y
# Clone the source code repository and build the Maven artifact 
RUN git clone https://github.com/devopshydclub/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

# Copy generated artifact into the final image using tomcat as our build image
FROM tomcat:9-jre11
LABEL "Project"="Containerization_Project"
LABEL "Author"="CMT35"
# Remove the default tomcat application/artifact (from offical tomcat documentation)
RUN rm -rf /usr/local/tomcat/webapps/* 
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
# Start the Tomcat server as the default command
CMD ["catalina.sh", "run"]