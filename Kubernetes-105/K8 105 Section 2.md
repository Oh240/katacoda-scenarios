## Kubernetes 105, Section 2: Creating Secrets 

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---

## Overview of Secrets 

Kubernetes Secrets let you store and manage sensitive information, such as passwords, OAuth tokens, and ssh keys. Storing confidential information in a Secret is safer and more flexible than putting it verbatim in a Pod definition or in a container image. See Secrets design document for more information.

A Secret is an object that contains a small amount of sensitive data such as a password, a token, or a key. Such information might otherwise be put in a Pod specification or in an image. Users can create Secrets and the system also creates some Secrets.

---

In this scenario, we're going to be decoding the username and password of the secrets.yml file. 

By default, Kubernetes requires data stored in Secrets to be base64 encoded (which they are). 


Display the contents of secret.yml. 
`cat secret.yml
`{{execute}}


Decode the username:
`echo -n 'YWRtaW4=' | base64 -d
`{{execute}}
---

Dcode the password:
`echo -n 'cGFzc3dvcmQ=' | base64 -d
`{{execute}}

---

Apply the Secrets:
`kubectl apply -f secret.yml
`{{execute}}
