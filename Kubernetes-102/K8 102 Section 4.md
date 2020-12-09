## Kubernetes 102, Section 4: Applying the YML File

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---

We know since this is a sandboxed environment, the cluster will be "default". If this were a local machine, we would have to ensure we're pointed to the proper cluster before applying the YML file to our Kubernetes cluster with the command below. 

`kubectl config current-context
`{{execute}}

---

`kubectl apply -f deployment.yml
`{{execute}}

deployment.apps/a123456-deployment created

To check that the deployment is there, run the command below to list all the deployments within your Kubernetes cluster and check for the existence of your username. You should see something similar to what is shown below.


`kubectl get deployments
`{{execute}}


Let's now check the status of the deployment with the command below. 

`kubectl get all -l user=a123456
`{{execute}}

---

Notice that there is something called a ReplicaSet. Under the hood, a Deployment actually creates a ReplicaSet, which is responsible for maintaining the number of replicas for the Pod that you specified in your Deployment.


Find your output! Use kubectl logs and then the name of your pod to see the output.


`kubectl -n default logs deployment/a123456-deployment --tail=10
`{{execute}}

"Hello world!" Should be displayed

Congrats! Your first Kubernetes Pod is live!

kubectl logs is a command that views the stdout and stderr from Pods.

Now let's delete a single pod and see what happens.

---

`kubectl delete pod $(kubectl get pod --selector="user"="a123456" -o jsonpath={.items[0]..metadata.name})
`{{execute}}

Deleting a pod will take some time to delete, so please be patient. 

pod "a123456-deployment-xxxx-xxxx" deleted

Notice that the pod name is different from the one before, this means that Kubernetes deployed a new pod when the pod gets deleted.

Now let's see everything created under the user "a123456". 

`kubectl get all -l user=a123456
`{{execute}}

Now let's try deleting the deployment.

`kubectl delete deploy -l user=a123456
`{{execute}}

deployment.apps "a123456-deployment" deleted
And check what is happening to the Pods


`kubectl get all -l user=a123456
`{{execute}}

Run the command again and see what happens. After a few moments, all Pods tied to the Deployment will be deleted.

---

`kubectl get all -l user=a123456
`{{execute}}

"No resources found" should be displayed. 
