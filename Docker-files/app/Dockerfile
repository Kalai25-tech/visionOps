FROM maven:3.9.9-eclipse-temurin-21-jammy AS build-stage
RUN git clone https://github.com/Kalai25-tech/visionOps.git
RUN cd visionOps/ && git checkout v1  && mvn install

# Runtime stage
FROM tomcat:10-jdk21

RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build-stage visionOps/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
