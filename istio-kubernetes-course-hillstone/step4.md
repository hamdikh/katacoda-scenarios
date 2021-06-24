The Bookinfo Example.

## Task

Istio made available a bookinfo application to explain how we can use it, let us deploy it and see what happens

`kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml`{{execute}}

Once everything is deployed, let us see our pods and services

`kubectl get services`{{execute}}

Wait a little bit until our pods are made available 

`kubectl get pods`{{execute}}

You can add **-w** to the previous command to watch the pods get ready  

Let us now see if we can access the product micro service 

`kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -sS productpage:9080/productpage | grep -o "<title>.*</title>"`{{execute}}

But this command isn't working ! what's going on ? why can't i access my app ? 
