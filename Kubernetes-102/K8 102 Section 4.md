## Applying the YML File
 Deployment

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---

```
Before we can apply the YML file to our Kubernetes cluster, we need to make sure that we are pointed towards the right cluster. In this case kind-kind is the correct cluster . Run the below command to find that out.


Run the below command

`kubectl config current-context
`{{execute}}


After confirming that we are pointed to the right Kubernetes cluster, we can now apply the YML file to that cluster.

---

`kubectl apply -f deployment.yml
`{{execute}}

deployment.extensions/a123456-deployment created

To check that the deployment is there, run the below command to list all the deployments within your Kubernetes cluster and check for the existence of what you changed a123456 to. You should see something similar to what is shown below.


`kubectl get deployments
`{{execute}}


Let's now check the status of the deployment. Make sure to replace the user according to what you changed it to be.

---

`kubectl get all -l user=a123456
`{{execute}}


Notice that there is something called a ReplicaSet. Under the hood, a Deployment actually creates a ReplicaSet, which is responsible for maintaining the number of replicas for the Pod that you specified in your Deployment.


Find your output! Use kubectl logs and then the name of your pod to see the output.


`kubectl logs pod/a123456-deployment-865fbbf84f-w9g5g
`{{execute}}

"Hello world!" Should be displayed

Congrats! Your first Kubernetes Pod is live!

kubectl logs is a command that views the stdout and stderr from Pods.

Now let's delete the pod and see what happens.

---

`kubectl delete pod/a123456-deployment-865fbbf84f-w9g5g
`{{execute}}

pod "sample-deployment-69f948f6f9-wh9sb" deleted

Notice that the pod name is different from the one before, this means that Kubernetes deployed a new pod when the pod gets deleted.


`kubectl get all -l user=a123456
`{{execute}}

Now let's try deleting the deployment.

---

`kubectl delete deploy -l user=a123456
`{{execute}}

deployment.extensions "a123456-deployment" deleted
And check what is happening to the Pods


`kubectl get all -l user=a123456
`{{execute}}

Run the command again and see what happens. After a few moments, all Pods tied to the Deployment will be deleted.

---

`kubectl get all -l user=a123456
`{{execute}}

No resources found.

Alternatively, you can also delete objects from Kubernetes using the .yml file that you applied them with.


`kubectl delete -f deployment.yml
`{{execute}}

deployment.extensions "a123456-deployment" deleted

---
