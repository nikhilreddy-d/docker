FROM maven:3-amazoncorretto-17 AS builder
COPY . /spring-petclinic
RUN  cd /spring-petclinic && mvn package

FROM amazoncorretto:11-alpine3.17
LABEL author="nikhil"
LABEL organization="practice"
ARG DOWNLOAD_LOCATION='https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar'
ARG USERNAME='petclinic'
ARG HOMEDIR='/petclinic'
ENV TEST=hello
RUN adduser -h ${HOMEDIR} -s /bin/sh -D ${USERNAME}
USER ${USERNAME}
WORKDIR ${HOMEDIR}
ADD --chown=${USERNAME}:${USERNAME} ${DOWNLOAD_LOCATION} "${HOMEDIR}/spring-petclinic-2.4.2.jar"
EXPOSE 8080
CMD ["java", "-jar", "spring-petclinic-2.4.2.jar"]