##Creating and Referencing a ConfigMap
 Deployment

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---


```
Select ConfigMap.

Config-map.yml

Now deploy the below yaml file, this will reference the configmap in your deployment and deploy the service. 
Configmap-dep2.yaml

Test connectivity to nginx:
`kubectl run -n sandbox -i --rm --restart=Never curl-test --generator=run-pod/v1 --image=radial/busyboxplus:curl -- sh -c "curl -vvv hello-service-o719580.sandbox.svc.cluster.local"
`{{execute}}
pod "curl-test" deleted
