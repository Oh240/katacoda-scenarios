## Kubernetes 105, Section 2: Creating Secrets 

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---
In this lab, we're going to be decoding the username and password of the secrets.yml file. 

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
