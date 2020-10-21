## Test Logging Into Test Manager UI
 Deployment

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---

```The environment variables we defined are the username and password for the Tomcat Manager UI. This is found at http://tomcat-server:8080/manager/html
Exec into the Tomcat Pod and curl localhost/manager and check the response code:
To do this, we first need the name of the Tomcat Pod
`kubectl get pods -l user=a123456
`{{execute}}
 
 ---
 
 
The below command Exec’s into the Pod, curls localhost, returns output, looks for response code, then exits the exec session:
`kubectl exec -it tomcat-a123456-99464c7d4-lkwxc -- sh -c "curl -is localhost:8080/manager/html | grep HTTP"
`{{execute}}
HTTP/1.1 401
This should return HTTP/1.1 401 because we did not specify a username and password.

---
The below command Logs in using the username and password defined in the Secret, ensures the -is is lower case and not upper when using curl:
`kubectl exec -it tomcat-a123456-849bbb4c6c-llcg8 -- sh -c "curl –is -u admin:password localhost:8080/manager/html | grep HTTP" HTTP/1.1 200
`{{execute}}
This should return HTTP/1.1 200

