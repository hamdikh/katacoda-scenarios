The Bookinfo Example.

## Task

Let us 
`kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml`{{execute}}

`kubectl get services`{{execute}}

`kubectl get pods`{{execute}}


RAS aucun accès à l'application
`kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -sS productpage:9080/productpage | grep -o "<title>.*</title>"`{{execute}}

