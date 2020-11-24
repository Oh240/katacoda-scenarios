## Kubernetes 105, Section 2: Creating Secrets 

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---

Insert the Secrets as environment variables into the Pod in the Tomcat Deployment and save it as deploy3.yaml or deploy3.yml:

`deploy3.yml
`{{execute}}
---

Apply the Deployment and the Service:

`kubectl apply -f deploy3.yml
`{{execute}}

---


It will state “deployment.extensions/tomcat-a123456 created 
service/tomcat-service-a123456 created”
