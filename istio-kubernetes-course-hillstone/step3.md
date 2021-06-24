First Example - Nginx

## Task

Let us run an nginx pod and see what happens

`kubectl run nginx --image=nginx`{{execute}}

verify your pod using the following command

`kubectl get pods`{{execute}}

Huh ! how come ? what's going on ? why do we have two containers running ?

Let us inspect the pod

`kubectl get pod nginx -oyaml`{{execute}}


