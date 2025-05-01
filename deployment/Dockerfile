FROM gradle:8.7-jdk21 AS build
WORKDIR /app

# Copiar el proyecto completo, desde el contexto superior
COPY --chown=gradle:gradle . /app

RUN gradle clean build -x test

FROM eclipse-temurin:21-jdk-alpine
VOLUME /tmp

COPY --from=build /app/applications/app-service/build/libs/*.jar OpenArc.jar

ENV JAVA_OPTS=" -Xshareclasses:name=cacheapp,cacheDir=/cache,nonfatal -XX:+UseContainerSupport -XX:MaxRAMPercentage=70 -Djava.security.egd=file:/dev/./urandom"
# Replace with a non-root user to avoid running the container with excessive privileges
USER appuser
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS  -jar OpenArc.jar" ]