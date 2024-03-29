# Testifi
Testifi takes [Apifi](https://github.com/sindaryn/apifi) to the next level by autogenerating integration tests for all autogenerated GraphQL resolvers. It integrates with [Mockeri](https://github.com/sindaryn/mockeri) to combine intelligent data mocking with all integration tests.

## Overview
The purpose of this library is to provide a **rudimentary** level of integration testing against APIs created with [Apifi](https://github.com/sindaryn/apifi). It does so by using the [Mockeri](https://github.com/sindaryn/mockeri) library to generate sufficient mock data to perform the necessary testing, and then executing CRUD operations against each resolver in the API schema. The objective is to ensure that the API _basically_ works. Obviously, this tool is no replacement for whichever edge-case testing may be necessary in any given use case. That is up to the developer. However, simple flaws in datamodel design, underlying infrastructure and configuration flaws, etc. are detectable using these autogenerated tests. 

## A few friendly suggestions
1. Please aquaint yourself with both [Apifi](https://github.com/sindaryn/apifi) and [Mockeri](https://github.com/sindaryn/mockeri) prior to using this library.
2. Use this tool with several fine grains of salt ;)

## Installation
Testifi can be installed using [jitpack](https://jitpack.io/), as follows:
#### Maven
Testifi is available on maven central:
```
<dependency>
    <groupId>org.sindaryn</groupId>
        <artifactId>testifi</artifactId>
    <version>0.0.1</version>
</dependency>
```

### Requirements
1. The main class must be annotated either with `@SpringBootApplication`, or `@MainClass`.
2. All entities **must** have a public `getId()` method.

## Activation
As previously stated, this library relies on [Mockeri](https://github.com/sindaryn/mockeri) for generating data to test against. Therefore, in order to signal to Mockeris' `DatabasePopulator` bean to go ahead and populate the database with mock data, the environment varaible `DUMMY_POPULATE=true` must be exported, prior to running or debugging the project.

## Detailed instructions
Plug, play & debug.

## Known Issues
The [`getAsEmbeddedCollection`](https://github.com/sindaryn/testifi/blob/master/src/main/java/org/sindaryn/testifi/service/TestLogic.java#LC287) test can be unreliable when evaluating self referencing many to many relationships.

#### That's all for now, happy coding!
    
### License
Apache 2.0