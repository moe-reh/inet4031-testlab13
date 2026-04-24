# Docker Lab: Containerizing a Three-Tier Application
**INET 4031 - Introductions to Systems**

This lab introduces Docker and Docker Compose by having you containerize a
real, multi-service application. You will package three components: Apache,
Flask, and MariaDB. These will be packaged into separate containers and wired together so they function as a complete application.

The application code and scaffolding are provided. Your job is to complete the Dockerfiles, verify the stack runs correctly, and document your work below.

> **Directions and explanations for this lab are on the repository Wiki.**
> Refer to the Wiki pages for step-by-step instructions.

---

# Project Overview
This application creates a IT help desk ticketing system using a container. The project will utilize and showcawses how Apache, Flash, and MariaDB work together in a "stack".

The goal of this project is to use Docker to automatate the creation of a web server. Instead of manually installing databases and web servers on your computer, we package each part into a "container." This allows a user to interact with a web interface that pulls data from a database through a backend API (Flask), all while ensuring the environment is identical for everyone.

# Prerequisites
Before running this lab, ensure your Virtual Machine (VM) or local environment has the following installed:

1. Docker: The engine that runs the containers.
2. Docker Compose: A tool used to define and run multi-container applications using a single YAML file.
3. Git: To clone the repository.
4. Sudo Privileges: Most Docker commands require administrative permissions on Linux.

# Getting Started
1. Clone the Repository: git clone https://github.com/moe-reh/inet4031-testlab12.git or https://github.com/moe-reh/inet4031-testlab13.git
2. Create your Environment File: cp .env.example .env
3. Build and Start the Containers: sudo docker-compose up --build -d
4. Verify the Containers are Running: sudo docker ps

# Configuration

We use a .env file to manage sensitive information and configuration settings. It contains variables like:
MYSQL_ROOT_PASSWORD: The master password for the database.
MYSQL_DATABASE: The name of the specific database being created.
DB_HOST: The name of the database service so Flask knows where to look.
The env file is not provided a teammate would need to create their own .env file based on the provided .env.example to ensure their local database has the correct credentials.

# Verification
To confirm that the entire stack is wired correctly and communicating, follow these steps:

Web Access: Open your browser and go to http://localhost:8080 (or your VM's IP). You should see the Apache landing page.
Run the Check Script: We have included a verification script to automate the testing of the connections between Apache, Flask, and MariaDB.

# lab13 - Kubernetes
This lab moved the application to run on Kubernetes instead of Docker Compose. The app is now maaged using kubernetes resources:
1. Pods: Runs one or more containers, represents an instance of the application.
2. Deployments: Manages the Pods, handles updates and replacements of Pods in the event of crashes or deletions in order to keep the application online.
3. Services: Connects users & apps to the pods. Stable way to access the app and route traffic to the pods. 

To deploy the application in Kubernetes run the following command: kubectl apply -f k8s/
The command above will create all the neccessary resources defined in the "k8s" folder.

Access the dashboard using: http://"your server IP":30080

# Feedback (Optional)
I really enjoyed this lab, and if I'm being honest I learned the most conceptually when completing the research questions, then the technical parts made that knowledge practical. I believe asing a couple of questions for us to research to then letting us complete technical work related to the question is a great combo for fortifying the learnings of the lab. I liked learning about pod, services, and deployements, their functionalities/limits, and being guided through how they actually work together to create an enviroment for an application. 

