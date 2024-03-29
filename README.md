# Supersonic Subatomic Integration with Apache Camel and Quarkus

This project uses [Apache Camel](https://camel.apache.org/) running on top of [Quarkus](https://quarkus.io/) to
demonstrate creating cloud-native, scalable, enterprise integration patterns quickly and effectively.

## Running The Mastodon Example

The public feed from any given Mastodon instance is accessible without authentication. You will only need to authenticate
with a Mastodon instance if you wish to write something to the API (e.g. Toot, Re-toot, Star, etc...)

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```shell script
./mvnw compile quarkus:dev
```

> **_NOTE:_**  Quarkus now ships with a Dev UI, which is available in dev mode only at http://localhost:8080/q/dev/.

## Packaging and running the application

The application can be packaged using:
```shell script
./mvnw package
```
It produces the `quarkus-run.jar` file in the `target/quarkus-app/` directory.
Be aware that it’s not an _über-jar_ as the dependencies are copied into the `target/quarkus-app/lib/` directory.

The application is now runnable using `java -jar target/quarkus-app/quarkus-run.jar`.

If you want to build an _über-jar_, execute the following command:
```shell script
./mvnw package -Dquarkus.package.type=uber-jar
```

The application, packaged as an _über-jar_, is now runnable using `java -jar target/*-runner.jar`.

## Creating a native executable

You can create a native executable using: 
```shell script
./mvnw package -Pnative
```

Or, if you don't have GraalVM installed, you can run the native executable build in a container using: 
```shell script
./mvnw package -Pnative -Dquarkus.native.container-build=true
```

You can then execute your native executable with: `./target/supersonic-subatomic-camel-1.0.0-SNAPSHOT-runner`

If you want to learn more about building native executables, please consult https://quarkus.io/guides/maven-tooling.

## Related Guides

- Camel Vert.x ([guide](https://camel.apache.org/camel-quarkus/latest/reference/extensions/vertx.html)): Send and receive messages to/from Vert.x Event Bus
- Camel Core ([guide](https://camel.apache.org/camel-quarkus/latest/reference/extensions/core.html)): Camel core functionality and basic Camel languages: Constant, ExchangeProperty, Header, Ref, Simple and Tokenize
- Camel Direct ([guide](https://camel.apache.org/camel-quarkus/latest/reference/extensions/direct.html)): Call another endpoint from the same Camel Context synchronously
- Camel JSON-B ([guide](https://camel.apache.org/camel-quarkus/latest/reference/extensions/jsonb.html)): Marshal POJOs to JSON and back using JSON-B
- Camel SmallRye Reactive Messaging ([guide](https://camel.apache.org/camel-quarkus/latest/reference/extensions/smallrye-reactive-messaging.html)): Camel integration with SmallRye Reactive Messaging
- Camel Stream ([guide](https://camel.apache.org/camel-quarkus/2.16.x/reference/extensions/stream.html)): Read and write from local or remote HTTP streams
- Camel GSon ([guide](https://camel.apache.org/camel-quarkus/2.16.x/reference/extensions/gson.html)): Marshal to and Unmarshal from JSON using Google's GSon library
