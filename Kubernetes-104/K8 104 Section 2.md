## Kubernetes 104, Section 2: Creating and Referencing a ConfigMap

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---

Deploy ConfigMap.

`kubectl apply -f config-map.yml
`{{execute}}

Now deploy the below yml file, this will reference the configmap in your deployment and deploy the service.

`kubectl apply -f configmap-dep2.yml
`{{execute}}

---

Test connectivity to nginx:
`kubectl run -n default -i --rm --restart=Never curl-test --generator=run-pod/v1 --image=radial/busyboxplus:curl -- sh -c "curl -vvv hello-service-a123456.default.svc.cluster.local"
`{{execute}}


pod "curl-test" deleted
