FROM openjdk:8-jdk-alpine

LABEL maintainer="udhayapps@gmail.com"

ARG PORT=$SIDECAR_SERVICE_PORT

ENV JAVA_OPTS $JAVA_OPTS
ENV PORT $PORT

EXPOSE $PORT

COPY sidecar.jar /

CMD java $JAVA_OPTS \
    -Djava.security.egd=file:/dev/./urandom \
    -Deureka.client.service-url.defaultZone=$EUREKA_SERVER_URI \
    -Dspring.cloud.config.uri=$CONFIG_SERVER_URI \
    -Dspring.profiles.active=$PROFILE \
    -jar /sidecar.jar \
    --server.port=$PORT
