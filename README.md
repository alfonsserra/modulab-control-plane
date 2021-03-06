[![Build Status](https://travis-ci.org/systelab/saas-control-plane.svg?branch=master)](https://travis-ci.org/systelab/saas-control-plane)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/7ce4e563c45b4d09a975d61bed7d5d50)](https://www.codacy.com/app/alfonsserra/saas-control-plane?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=systelab/saas-control-plane&amp;utm_campaign=Badge_Grade)
[![Known Vulnerabilities](https://snyk.io/test/github/systelab/saas-control-plane/badge.svg?targetFile=pom.xml)](https://snyk.io/test/github/systelab/saas-control-plane?targetFile=pom.xml)

# AWS Application Control Plane


## Getting Started

To get you started, simply clone the `saas-control-plane` repository and install the dependencies:

### Prerequisites

You will need [git][git] to clone the `saas-control-plane` repository, [OpenJDK 11][jdk-download] and [Maven][maven].

### Clone `saas-control-plane`

Clone the `saas-control-plane` repository with the following command:

```bash
git clone https://github.com/systelab/saas-control-plane.git
cd saas-control-plane
```

### Install Dependencies

In order to install the dependencies and generate the Uber jar, run:

```bash
mvn clean install
```

### Run

To launch the server, run:

```bash
cd target
java -jar saas-control-plane-1.0.jar
```

### Certificate

A self signed certificate is provided. The certificate was generated with the following commands:

```bash
keytool -genkey -keyalg RSA -alias selfsigned -keystore keystore.jks -storepass password -validity 365 -keysize 2048
keytool -importkeystore -srckeystore keystore.jks -destkeystore keystore.p12 -deststoretype pkcs12
```

> Do not use the certificate provided in production and never put any secret in your application.yml file.


## API

Swagger UI will be available at https://localhost:8443/swagger-ui.html and http://localhost:8080/swagger-ui.html 

First generate a token by login as user Systelab and password Systelab. Once done that, authorize Swagger by copying the bearer.

## Docker

### Build docker image

There is an Automated Build Task in Docker Cloud in order to build the Docker Image. 
This task, triggers a new build with every git push to your source code repository to create a 'latest' image.
There is another build rule to trigger a new tag and create a 'version-x.y.z' image

You can always manually create the image with the following command:

```bash
docker build -t systelab/saas-control-plane . 
```

### Run the container

```bash
docker run -p 8443:8443 -p 8080:8080 systelab/saas-control-plane
```

The REST Api will be available at https://localhost:8443/swagger-ui.html


[git]: https://git-scm.com/
[sboot]: https://projects.spring.io/spring-boot/
[maven]: https://maven.apache.org/download.cgi
[jdk-download]: https://adoptopenjdk.net/
[JEE]: http://www.oracle.com/technetwork/java/javaee/tech/index.html
[jwt]: https://jwt.io/
[cors]: https://en.wikipedia.org/wiki/Cross-origin_resource_sharing
[swagger]: https://swagger.io/
[allure]: https://docs.qameta.io/allure/
[junit]: https://junit.org/junit5/


