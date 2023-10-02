Mini-Clus-MP3 :- A Microservices  based MP4 to MP3 converter.
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Microservices-based Application README**

**Table of Contents**

- [Introduction](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#introduction)
- [Prerequisites](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#prerequisites)
- [Setup](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#setup)
  - [1. Install Docker](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#1-install-docker)
  - [2. Install Minikube](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#2-install-minikube)
  - [3. Install K9s](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#3-install-k9s)
- [Running the Application](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#running-the-application)
  - [1. Start Minikube](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#1-start-minikube)
  - [2. Deploy Microservices](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#2-deploy-microservices)
  - [3. Access the Services](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#3-access-the-services)
- [Services](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#services)
  - [Auth Service](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#auth-service)
  - [Gateway Service](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#gateway-service)
  - [Converter Service](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#converter-service)
  - [RabbitMQ Queue](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#rabbitmq-queue)
  - [Notification Service](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#notification-service)
- [Cleanup](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#cleanup)
- [Troubleshooting](https://chat.openai.com/c/480e9c2e-4849-47b9-a583-96b0606dd7f4#troubleshooting)

**Introduction**

This README provides instructions for setting up and running a Microservices-based application using Kubernetes, Docker, and Minikube. The application consists of the following services:

1. **Auth Service**: A Flask-based service for authentication.
1. **Converter Service**: A Flask-based service for converting data.
1. **RabbitMQ Queue**: A message broker for inter-service communication.
1. **Notification Service**: A Flask-based service for sending notifications.

The application is hosted on your local machine using Minikube, and it is managed using K9s, a Kubernetes management tool.

**Prerequisites**

Before you can run the application, ensure that you have the following prerequisites installed on your machine:

**1. Install Docker**

Docker is required to containerize and run the application services. You can download and install Docker from the official website: [Docker Installation Guide](https://docs.docker.com/get-docker/).

**2. Install Minikube**

Minikube is used to run a local Kubernetes cluster. You can install Minikube by following the instructions in the official documentation: [Minikube Installation Guide](https://minikube.sigs.k8s.io/docs/start/).

**3. Install K9s**

K9s is a terminal-based Kubernetes management tool. You can install K9s by following the instructions in the official documentation: [K9s Installation Guide](https://k9scli.io/topics/install/).

**Setup**

**1. Start Minikube**

Start Minikube with the following command:

bashCopy code

minikube start 

**2. Deploy Microservices**

Use Kubernetes manifests to deploy the microservices and RabbitMQ queue. You can find the manifests in the **kubernetes** directory of this repository.

bashCopy code

kubectl apply -f kubernetes/ 

**3. Access the Services**

Once the services are deployed, you can access them using the appropriate URLs and ports. You can use **kubectl get services** to view the exposed ports and IP addresses.

**Services**

![](Aspose.Words.f0780453-e665-482a-8992-93e59fb267ae.001.png)

**Auth Service**

The Auth Service provides authentication functionality. It is accessible at:

- URL: [http://localhost:{auth-service-port}](http://localhost:%7Bauth-service-port%7D/)
- Port: Exposed port for the Auth Service

![](Aspose.Words.f0780453-e665-482a-8992-93e59fb267ae.002.png)

Gateway Service

The Gateway Service acts as an API gateway for the other services. It is accessible at:

- URL: http://localhost:{gateway-service-port}
- Port: Exposed port for the Gateway Service

![](Aspose.Words.f0780453-e665-482a-8992-93e59fb267ae.003.png)

**Converter Service**

The Converter Service converts data. It is accessible at:

- URL: [http://localhost:{converter-service-port}](http://localhost:%7Bconverter-service-port%7D/)
- Port: Exposed port for the Converter Service

**RabbitMQ Queue**

RabbitMQ is a message broker used for communication between services. It is accessible at:

- URL: RabbitMQ does not have a direct URL; it is accessed internally by the services.
- ![](Aspose.Words.f0780453-e665-482a-8992-93e59fb267ae.004.png)
- Command to send a request:
  ![](Aspose.Words.f0780453-e665-482a-8992-93e59fb267ae.005.png)
- ![](Aspose.Words.f0780453-e665-482a-8992-93e59fb267ae.006.png)

**Notification Service**

The Notification Service sends notifications. It is accessible at:

- URL: [http://localhost:{notification-service-port}](http://localhost:%7Bnotification-service-port%7D/)
- Port: Exposed port for the Notification Service

**Cleanup**

To clean up the resources and stop Minikube, you can use the following command:

bashCopy code

minikube delete 

**Troubleshooting**

If you encounter any issues while setting up or running the application, refer to the troubleshooting section in the official documentation for Docker, Minikube, and K9s. Additionally, check the logs of the individual services using **kubectl logs <pod-name>** for debugging purposes.

