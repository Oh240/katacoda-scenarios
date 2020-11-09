## Question (4/6)

Note: All questions are mandatory. Once completed, click on the 'Check Answers' button to validate and continue to the next question.


## The Role of Kubernetes 

Kubernetes is not the actual engine that is running your containerized applications. Kubernetes is the orchestrator of Docker containers and it does not exist without a container runtime. Founded by Google, Kubernetes is the container-orchestration system for automating application deployment, scaling, and management. In terms of a CI/CD pipeline, Kubernetes is the Continuous Delivery component. 

## How It Works 

Under the hood, Kubernetes is calling Docker and sending it tasks based off of specifications that a user declares. A user tells Kubernetes what to do with Docker containers via kubectl commands and YAML files, the ways in which you collect information and declare Objects within Kubernetes. Kubectl (pronounced kube control... be careful how you pronounce it, it's a big deal for some) is a command line tool used for interacting with a Kubernetes cluster. Once Kubernetes is told what to do with a container, it takes over from there. You will never need to use Docker commands with Kubernetes once the image is built. Kubernetes allows you to control where a container runs, the amount of resources it can consume, what applications it can talk to, the number of instances of the container, and much more.

>>Q4: What does Kubernetes allow you to control? Select all that apply. << 
[*]Kubernetes allows you to control where a container runs
[]VM's running on your network
[*]The number of instances of the container
[]Kubernetes resource management
