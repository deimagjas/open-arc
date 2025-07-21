FROM eclipse-temurin:21-jdk-alpine
VOLUME /tmp
COPY applications/app-service/build/libs/OpenArc.jar OpenArc.jar
# Crear usuario appuser sin privilegios
RUN adduser -D -u 1001 appuser
USER appuser
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Dserver.port=${PORT:-8080} -jar OpenArc.jar" ]
EXPOSE 8080