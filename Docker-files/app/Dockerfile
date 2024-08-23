FROM openjdk:11 AS BUILD
RUN apt update && apt install maven -y
RUN git clone https://github.com/devopshydclub/vprofile-project.git
RUN cd vprofile-project && git checkout docker
RUN mvn install

FROM tomcat:9-jre11
RUN rm -rf /user/local/tomcat/webapps/*
COPY --from=BUILD vprofile-project/target/vprofile-v2.war /user/local/tomcat/webapps/ROOT.war
CMD ["catalina.sh", "run"]

EXPOSE 8080
