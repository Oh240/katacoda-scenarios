## Kubernetes 103, Section 2: Accessing a Service
---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---

## Demo for Accessing a Service 

Now that we have a web server running and a service bound to it, we are able to access it from within the Kubernetes cluster. We can test this by deploying a new Pod in the cluster, shelling into it, and then curling the IP or DNS entry for the service.


Deploy the Pod and curl the Service from within the Pod:

Step 1: 

`kubectl run -n default -i --rm --restart=Never curl-test --generator=run-pod/v1 --image=radial/busyboxplus:curl -- sh -c "curl -vvv hello-service-a123456.default.svc.cluster.local"
`{{execute}}

---

## Explanation of Deploying a Pod and Helpful Tips

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

We can also access our nginx deployment by using kubectl port-forward. It is worth noting that kubectl port-forward does not require a service as you can bind a Pod's port directly to localhost. kubectl port-forward should only be used for development and testing and is not practical for production deployments. There are other Types of Kubernetes services that are better suited for production.

---

Step 2:

Port Forward the nginx Pod to localhost:80

`kubectl port-forward $(kubectl get pod --selector="user"="a123456" -o jsonpath={.items[0]..metadata.name}) --address 0.0.0.0 8080:80
`{{execute}}
Forwarding from 0.0.0.0:8080 -> 80 Forwarding from [::1]:80 -> 80

Navigate to the dashboard tab, to the right of the terminal tab and enter "8080" as the port number. Then select "Display Port" and a "Welcome to nginx" screen should appear. Note that if you delete your Pod, a new one will be deployed by your Deployment, but you will have to re-run the kubectl port-forward command as your pod is now under a different name. 

---

Step 3:

Once you're finished, stop the port forward with control + c and you can remove everything with the below command:
`kubectl delete svc,deploy -l user=a123456
`{{execute}}

It should display deployment.apps "hello-web-a123456" deleted
