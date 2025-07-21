FROM eclipse-temurin:21-jdk-alpine
VOLUME /tmp
COPY applications/app-service/build/libs/OpenArc.jar OpenArc.jar
USER appuser
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Dserver.port=${PORT:-8080} -jar OpenArc.jar" ]
EXPOSE 8080