# Projet student-list 
Information about the owner
Session eazytraining : Bootcamp DevOps N°15
First & Last Name : Paterne arthur ATANGANA
LinkedIn : [https://www.linkedin.com/in/paterne-arthur-atangana-532366b5]


## Context


*POZOS*  is an IT company located in France and develops software for High School.

The innovation department want to disrupt the existing infrastructure to ensure that

it can be scalable, easily deployed with a maximum of automation.

POZOS wants you to build a **POC** to show how docker can help you and how much this technology is efficient.

For this POC, POZOS will give you an application and want you to build a "decouple" infrastructure based on **Docker**.

Currently, the application is running on a single server with any scalability and any high availability.

When POZOS needs to deploy a new release, every time some goes wrong.

In conclusion, POZOS needs agility on its software farm.

## Objectives

Our job is to create microservices from the provided source code in order to containerize an application with two modules (frontend and backend).
First, I set up my infrastructure from a virtual machine running the Centos7 operating system. I'll then build using Dockerfile and Docker-compose and once the tests are correct I'll move on to deployment 

## Infrastructure

My work includes:
1. Use Virtualbox as a hypervisor to create a virtual machine
2. Use Vagrant as an infrastructure configurator to manage virtual machines
3. Install Docker and Docker-compose on the virtual machine
4. Create a container for each module (backend and frontend)
5. Let containers interact with each other
6. Provide a private registry to store images delivery.


## Build and test

Step N°1 :
I need to clone the project first
![etape 1](https://github.com/paterneatango/student-list/assets/147111228/2b8b4641-959c-495d-b4d3-71d1f7efc9be)

Step N°2 :
Edit the DockerFile
![etape 2](https://github.com/paterneatango/student-list/assets/147111228/fdda2073-a1c0-4984-8094-97627a13b991)

Step N°3 :
Move back to the root directory of the project and run the backend api container with those arguments :
#Move back to the root directory of the project
cd ..
#build the api 
docker build -t api .
#Run the backend api container and verify the container
![docker images (etape 4 docker RUN)](https://github.com/paterneatango/student-list/assets/147111228/47f44a92-bfc2-4236-b08f-1570249a77fe)
#test the backend
![docker images (etape 5 test curl du frontend)](https://github.com/paterneatango/student-list/assets/147111228/21c8c964-401f-42cd-bb98-13d64110d363)

Step N°4 : Runing le Fronted webapp container
Edit the docker-compose
![docker-compose images (etape 6 Frontend et backend)](https://github.com/paterneatango/student-list/assets/147111228/181c91b3-5e93-4d83-aacf-982039ee93ca)

Step N°5 : Updating index file
You need to update the following line before running the website container to make api_ip_or_name and port fit your deployment $url = 'http://<api_ip_or_name:port>/pozos/api/v1.0/get_student_ages';
api_ip_or_name: the DNS name of the container (api)
port: the external port of the API (5000)
![index php](https://github.com/paterneatango/student-list/assets/147111228/ff28c6fb-fbac-40a1-865c-825ef765dd7a)

Step N°6 : Deployemnt
#Start docker-compose 
![docker-compose images (etape 7 demarrer le)](https://github.com/paterneatango/student-list/assets/147111228/bb65b412-2d17-4e32-bceb-ad5c9644cd94)
#check the app
![docker-compose images (etape 8)](https://github.com/paterneatango/student-list/assets/147111228/b17ce25f-1415-4a36-bb65-214cc4b33cb8)
#Test the communication between the two apps
![Affichage](https://github.com/paterneatango/student-list/assets/147111228/ed2dafe9-fa60-4dba-b8ac-f5b07451517f)
#Tag My Image Container 
![taguer mon image](https://github.com/paterneatango/student-list/assets/147111228/feaa3b62-f0cf-4563-8d19-68e8be8370e6)

Step N°7 : Create a registry and its frontend
registry:2 image for the registry, and joxit/docker-registry-ui:static for its frontend gui 
#Edit the docker-compose
![conteneur registry](https://github.com/paterneatango/student-list/assets/147111228/6359b9e7-57b2-4760-9167-310051a7f9b5)
#restart docker-compose
![registry docker-compose up](https://github.com/paterneatango/student-list/assets/147111228/57a8dc46-ba4e-4179-b71b-31d7718e79b6)
#Run
Start the private registry in My Network to communicate with other containers 
![registre etape 8](https://github.com/paterneatango/student-list/assets/147111228/8ca49cac-7773-47eb-8b1f-89036261c369)
#Interface od registry
![interface registre](https://github.com/paterneatango/student-list/assets/147111228/887c92a1-b7a7-4105-a622-e486bcf4627e)

## The files and their roles
My render contains five main files:
• simple_api/Dockerfile: Create an API image using the source code it contains
• docker-compose.yml: launch applications (APIs and web applications)
• simple_api/student_age.py: Contains the source code for the Python API
• simple_api/student_age.json: Contains the student's name and age in JSON format.
• index.php: The PHP page on which the end user will log in and interact with the service to list students and their ages.

## Conclusion
Through this project, I had the opportunity to set up Docker images, volumes, and deploy containers using docker-compose. This allowed me to strengthen my technical skills and gain a better understanding of the principles of microservices. So, by using Docker, we can deploy applications in microservices, where each service represents a scalable Docker image. I look forward to working on similar projects and helping to improve enterprise containerization processes.

First & Last Name : Paterne arthur ATANGANA
LinkedIn : [https://www.linkedin.com/in/paterne-arthur-atangana-532366b5]


