FROM gradle:7 AS base
ENV test1=test1
CMD ["bash"]

# build
FROM base AS test-and-build
ENV test2=test2
COPY . /workspace
WORKDIR /workspace
RUN ./gradlew build

# production
FROM openjdk:17 AS production
ENV test3=test3
COPY --from=test-and-build /workspace/build/libs/api-0.0.1-SNAPSHOT.jar ./api.jar
CMD ["java", "-jar", "api.jar"]
