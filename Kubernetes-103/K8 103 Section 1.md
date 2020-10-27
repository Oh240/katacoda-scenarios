## Kubernetes Services

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---

```
In order for the Pods within Kubernetes to communicate with each other, they must be bound to a Service. The beauty of Services in Kubernetes is that as Pods die and are redeployed, the Service that the application is bound to will route the traffic to the appropriate Pods as they become available. There is no need to manually go in and tell Kubernetes which Pods to route traffic to.

---

There are several different Types of Services in Kubernetes. The default one, and the one we will be using in this path, is ClusterIP. A service of type: ClusterIP gives an application an IP that is accessible from within the Kubernetes Cluster and a DNS entry that is accessible within the cluster.

---

First, let's create a deployment of nginx, it’s called deploy.yml. Select deploy.yml to run the script. 

Next, we need to apply the deployment deploy.yml to the cluster. Select the below command. 

`kubectl apply -f deploy.yml
`{{execute}}


After running the above command, “deployment.extensions/hello-web-a123456 created” will be displayed. 
---

Now, let's run a service so that our nginx Deployment is accessible within the cluster. The YML file is named service.yml. Select service.yml. 
Service.yml

---

Then, apply the service to the cluster. Select the below command. 
`kubectl apply -f service.yml
`{{execute}}

After running the above command, “service/hello-service-a123456 created” will be displayed. 

To check whether the service exists, you can run the below command:

`kubectl get services
`{{execute}}

---
NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE hello-service-a123456 ClusterIP 10.108.32.116 <none> 80/TCP 10s kubernetes ClusterIP 10.96.0.1 <none> 443/TCP 6d
Another way to ensure everything was deployed properly, is by running the below command. 

---

`kubectl get svc,deploy,po -l user=a123456
`{{execute}}

svc, deploy, and po are short for service, deployment and pod

In our service.yml, we did not specify a Type for our Service. Kubernetes automatically assigned it a Type of ClusterIP and gave it a cluster internal IP address over the port that we declared.


---
