# Supersonic Subatomic Integration with Apache Camel and Quarkus

This project uses [Apache Camel](https://camel.apache.org/) running on top of [Quarkus](https://quarkus.io/) to
demonstrate creating cloud-native, scalable, enterprise integration patterns quickly and effectively.

## Running The Twitter Example

Twitter requires a developer account and API tokens/keys to access their Search API. In order for this example to work you will need to
populate a `.env` file wherever you run the application from which looks like this:

```
TWITTER_ACCESS_TOKEN=<REDACTED>
TWITTER_ACCESS_SECRET=<REDACTED>
TWITTER_API_KEY=<REDACTED>
TWITTER_API_SECRET=<REDACTED>
```

You can get these values by signing up for a developer account at https://developer.twitter.com/

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
- Camel Vert.x WebSocket ([guide](https://camel.apache.org/camel-quarkus/latest/reference/extensions/vertx-websocket.html)): Camel WebSocket support with Vert.x
- Camel JPA ([guide](https://camel.apache.org/camel-quarkus/latest/reference/extensions/jpa.html)): Store and retrieve Java objects from databases using Java Persistence API (JPA)
- Camel Direct ([guide](https://camel.apache.org/camel-quarkus/latest/reference/extensions/direct.html)): Call another endpoint from the same Camel Context synchronously
- Camel JSON-B ([guide](https://camel.apache.org/camel-quarkus/latest/reference/extensions/jsonb.html)): Marshal POJOs to JSON and back using JSON-B
- Camel SmallRye Reactive Messaging ([guide](https://camel.apache.org/camel-quarkus/latest/reference/extensions/smallrye-reactive-messaging.html)): Camel integration with SmallRye Reactive Messaging
- Blaze-Persistence ([guide](https://quarkus.io/guides/blaze-persistence)): Advanced SQL support for JPA and Entity-Views as efficient DTOs
- Reactive PostgreSQL client ([guide](https://quarkus.io/guides/reactive-sql-clients)): Connect to the PostgreSQL database using the reactive pattern
- Reactive Routes ([guide](https://quarkus.io/guides/reactive-routes)): REST framework offering the route model to define non blocking endpoints
