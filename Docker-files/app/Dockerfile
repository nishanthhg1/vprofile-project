FROM openjdk:11 AS BUILD_IMAGE
LABEL "Project"="Vprofile"
LABEL "Author"="Nishanth"
RUN apt update && apt install maven -y
RUN git clone -b containers https://github.com/nishanthhg1/vprofile-project.git
RUN cd vprofile-project && mvn install

FROM tomcat:9-jre
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/ROOT.war
EXPOSE 8080
CMD ["catalina.sh","run"]