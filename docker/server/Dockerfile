FROM openjdk:11.0.3-jdk-stretch as build
COPY . /apps
WORKDIR /apps
ENV LANG C.UTF-8
#RUN ["./mvnw","clean", "-Dmaven.test.skip=true", "package"]
#
#FROM openjdk:11.0.3-jre-slim-stretch
#WORKDIR /apps
#COPY --from=build "/apps/target/atmosphere-0.0.1-SNAPSHOT.jar" /apps/app.jar
#
#CMD java -jar /apps/app.jar


# Copy maven executable to the image
COPY mvnw .
COPY .mvn .mvn

# Copy the pom.xml file
COPY pom.xml .

# Build all the dependencies in preparation to go offline.
# This is a separate step so the dependencies will be cached unless
# the pom.xml file has changed.
RUN ./mvnw dependency:go-offline -B

# Copy the project source
COPY src src

ENTRYPOINT ["./mvnw", "spring-boot:run"]
