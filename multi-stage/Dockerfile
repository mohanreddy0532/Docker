FROM    centos:7 AS compiler
RUN 	yum install epel-release -y
RUN     yum install maven -y
RUN     mkdir /app
WORKDIR /app
COPY    src .
COPY    pom.xml .
RUN     mvn package

FROM    java:8-alpine
COPY    --from=compiler /app/target/shipping-1.0-jar-with-dependencies.jar shipping.jar
CMD     ["java", "-jar", "shipping.jar"]