This is your first step.

## Task

First of all we need to configure our _kubernetes_ environment so all you need to do is launch a **command**

`launch.sh `{{execute}}

Once this is done, you need to verify the kubernetes _installation_ please type the following **command**

`kubectl get node `{{execute}}


`curl -L https://istio.io/downloadIstio | sh -`{{execute}}


`cd istio-1.10.1 && export PATH=$PWD/bin:$PATH `{{execute}}

`istioctl install`{{execute}}

`kubectl label namespace default istio-injection=enabled`{{execute}}

`kubectl run nginx --image=nginx`{{execute}}

`kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml`{{execute}}

`kubectl get services `{{execute}}

`kubectl get pods `{{execute}}

`kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -sS productpage:9080/productpage | grep -o "<title>.*</title>"` {{execute}}

`cat samples/bookinfo/networking/bookinfo-gateway.yaml `{{execute}}

`kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml `{{execute}}
