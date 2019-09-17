FROM frolvlad/alpine-oraclejdk8:slim
VOLUME /tmp
VOLUME /log
ADD spring-petclinic*.jar app.jar
ENTRYPOINT [ "sh", "-c", "java -jar /app.jar" ]