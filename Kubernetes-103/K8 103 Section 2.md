## Accessing a Service
 Deployment

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---


Now that we have a web server running and a service bound to it, we are able to access it from within the Kubernetes cluster. We can test this by deploying a new Pod in the cluster, shelling into it, and then curling the IP or DNS entry for the service.

Deploy the Pod and curl the Service from within the Pod:

`kubectl run -n sandbox -i --rm --restart=Never curl-test --generator=run-pod/v1 --image=radial/busyboxplus:curl -- sh -c "curl -vvv hello-service-a123456.sandbox.svc.cluster.local"
`{{execute}}

---


This method of deploying a Pod and testing connectivity to a Service is a handy troubleshooting technique.
-i : interactive, keep STDIN (standard input) open even if not attached
--rm : delete resources created in this command for attached containers
--restart=Never : creates a Pod by default if generator flag was not specified

curl-test : name of new Pod
--generator=run-pod/v1 : generate resources based on a set of inputs and is used to pin a particular behavior which may change in the future
--image=radial/busyboxplus:curl : this curl image was created as an alternate for those only needing to use curl to extract their configuration in their Hub containers.
-- sh : shelling into the new Pod
-c "curl -Is hello-service-a123456": -c means to run the command that is within the "" in the Pod.
-Is: within curl, the -I (CAPS i) fetch the headers only. The -s means silent or quiet mode which means to not show progress meter or error messages, making curl mute.

---

We can also access our nginx deployment by using kubectl port-forward. It is worth noting that kubectl port-forward does not require a service as you can bind a Pod's port directly to localhost. kubectl port-forward should only be used for development and testing and is not practical for production deployments. There are other Types of Kubernetes services that are better suited for production.

---

Port Forward the nginx Pod to localhost:80

`kubectl port-forward $(kubectl get pod --selector="user"="a123456" -o jsonpath={.items[0]..metadata.name}) 80:80
`{{execute}}
Forwarding from 127.0.0.1:80 -> 80 Forwarding from [::1]:80 -> 80

Now you are able to access your nginx Deployment from your browser at localhost by searching for localhost:80. Note that if you delete your Pod, a new one will be deployed by your Deployment, but you will have to re-run the kubectl port-forward command as your pod is now under a different name. 

---

You should see a similar image as shown below when access your nginx Deployment from your browser:


(./kubernetes-k3s/assets/nginx.PNG)

---

Once you're done, you can remove everything with the below command:
`kubectl delete svc,deploy -l user=a123456
`{{execute}}

It should display “service "hello-service-a123456"

deleted deployment.extensions "hello-web-a123456" deleted”

