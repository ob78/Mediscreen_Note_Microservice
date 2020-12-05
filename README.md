# Mediscreen - Note application
Welcome to Mediscreen !

- Mediscreen is a medical company specialized in diseases diagnosis
- Mediscreen wants to develop a new application which goal is to diagnose the risk for patients to develop diabetes

### Mediscreen Diabetes Application

The application is composed of 3 Microservices :
- Mediscreen Patient : in charge of managing patients and their personal data
- Mediscreen Note : in charge of managing notes written by doctors
- Mediscreen Rapport : in charge of generating reports evaluating the risk for patients to develop diabetes

This repository contains the Mediscreen Note Microservice.

You will find the other Microservices in the following repositories :
- Mediscreen Patient : <https://github.com/ob78/Mediscreen_Patient_Microservice/tree/develop>
- Mediscreen Rapport : <https://github.com/ob78/Mediscreen_Rapport_Microservice/tree/develop>

### Technologies used

Technologies used for this Microservice are the following.

BackEnd side :
- Java as programming language
- SpringBoot for the web application which is based on the MVC pattern
- Server is SpringBoot Tomcat embedded
- Gradle to run the tests, build and package the application
- MongoDB as database
- JUnit as tests engine
- Mockito as mocking framework for tests

FrontEnd side :
- HTML/CSS + Bootstrap for the views (User Interface)
- Thymeleaf as template engine

Microservices communicate using REST APIs.

### Getting Started

The following instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

You need to install the following software :

- Java 8
- Gradle 6.6.1
- MongoDB 4.4
- Docker + Docker-Compose
>You don't need to install SpringBoot by yourself because dependencies will be added by Gradle

### Installing

You will find below a step by step explanation that tell you how to get a development environment running :

1.Install Java :
<https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html>

2.Install Gradle :
<https://gradle.org/install/>

3.Install MongoDB :
<https://docs.mongodb.com/guides/server/install/>

4.Install Docker + Docker-Compose :
<https://docs.docker.com/get-docker/>

### Profiles and Configuration

Three Spring profiles are available for each following phase :

- PROD profile used for Production phase
- DEV profile used for Development phase
- TEST profile used for Test phase

There is a global Spring configuration properties file : application.properties, and a dedicated configuration properties file for each profile : application-*profileName*.properties. 
These files are stored in the src/main/resources directory for PROD and DEV profiles and in the src/test/resources directory for the TEST profile.

The URL (hostname + port) for the Patient Microservice can be configured in these files.

### DataBase creation and initialization

By default there is no username and password for connection to the database.
We kept this configuration for the sake of simplicity.

For the DEV profile, the database is initialized with some notes. This is done using the file : data.json.

### Application running

Then you can import and run the application from your favorite IDE.

>Please note that the application has been developed with the IntelliJ IDE.

### Endpoints

For information about EndPoints that are exposed by the Mediscreen Note Microservice, please refer to the document located in this repository called : 

### Docker container deployment

A Dockerfile is present in this repository in order to deploy the application in a Docker container.
>In order to build a Docker Image using this Dockerfile, please use the following command line (in the *Dockerfile* directory) :
`docker build -t note .`

When the Note Docker image is created, you can run the Microservice using the *docker-compose.yml* file located in this repository.
>To do this, please use the following command line (in the *docker-compose.yml* directory) :
`docker-compose up`
 
This will :
- Create and launch a MongoDB server in a container
- Launch the Note application in a container
- Create a dedicated Docker bridge network to enable their communication 
- Map the directory containing the MongoDB data in an external directory so that data are note lost if container is deleted

In order to run the whole application, i.e. the 3 Microservices, you can use the *docker-compose.yml* file that is located in the Rapport Microservice repository. 
 
### Tests

Tests are included. You can run them using JUnit runner or using Gradle.
