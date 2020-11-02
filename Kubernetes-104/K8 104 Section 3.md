## Kubernetes 104, Section 3: Editing a ConfigMap
 Deployment

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---


One of the benefits of using a ConfigMap is that they allow you to make edits to a Pod without having to redeploy. So to change our index.html page, rather than editing the nginx deployment itself, we can edit the ConfigMap.


Change the index.html page by editing your ConfigMap YAML. When you are done, apply it.

`kubectl apply -f configmap.yml
`{{execute}}

It will display “configmap/nginx-index-a123456 configured”

---


It may take a few moments for the changes to be applied. Under the hood, nginx is monitoring the ConfigMap. If a change is applied to the ConfigMap, it will write the new index.html file. All of this is done without a restart of the nginx Pod.
See the changes:


`kubectl run -n sandbox -i --rm --restart=Never curl-test --generator=run-pod/v1 --image=radial/busyboxplus:curl -- sh -c "curl -vvv hello-service-a123456.sandbox.svc.cluster.local"
`{{execute}}

It will display “pod "curl-test" deleted”
