## Kubernetes 105, Section 2: Creating Secrets 

---

**WARNING - YOU HAVE LESS THAN 1 HOUR BEFORE YOUR SESSION EXPIRES!**

>Note the time left (in HH:MM) for the session, it is in your prompt and updated after every command run:

![Terminal Time Remaining](./assets/term-expire.png)

---


By default, Kubernetes requires data stored in Secrets to be base64 encoded. For the Secret for the username we are going to define, we must first base64 encode the username.
`echo -n 'admin' | base64 YWRtaW4=
`{execute}

---

Apply secret.yml. 
`kubectl apply -f secret.yml
`{execute}

Base64 encode the password:
`echo -n 'password' | base64 cGFzc3dvcmQ=
`{execute}

---

Apply the Secrets:
$ kubectl apply -f secret.yml
