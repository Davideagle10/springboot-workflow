ARG APP_NAME=webapp

ARG APP_VERSION=0.0.1-SNAPSHOT

FROM amazoncorretto:17-alpine3.22

COPY build/libs/${APP_NAME}-${APP_VERSION}.jar .

CMD ["java", "-jar", "${APP_NAME}-${APP_VERSION}.jar"]