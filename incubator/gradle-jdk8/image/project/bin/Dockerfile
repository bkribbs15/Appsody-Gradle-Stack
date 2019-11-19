# Dockerfile for building your application.
# Defines the final image that contains content from both the image and template.
# dev.local/gradle-jdk8:SNAPSHOT
# {{APPSODY_STACK}}
FROM  appsody/gradle-jdk8:0.1 as compile


COPY . /project

WORKDIR /project

RUN ./gradlew build

COPY  ./build/libs/project.jar ./app.jar
# change permissions
RUN chmod go=rx ./app.jar
USER gradle

#CMD  ["java", "-jar", "build/libs/micro-customer-0.0.1.jar","--debug"]
# Pass control your application
ENTRYPOINT [ "sh", "-c", "exec java $JVM_ARGS -Djava.security.egd=file:/dev/./urandom -jar ./app.jar" ]

