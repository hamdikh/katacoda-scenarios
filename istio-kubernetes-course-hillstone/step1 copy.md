This is your first step.

## Task

First of all we need to configure our _kubernetes_ environment so all you need to do is launch a **command**

`launch.sh ` {{execute}}

Once this is done, you need to verify the kubernetes _installation_ please type the following **command**

`kubectl get node ` {{execute}}

Step 1 - Install Istio

`curl -L https://istio.io/downloadIstio | sh -` {{execute}}


`cd istio-1.10.1 && export PATH=$PWD/bin:$PATH ` {{execute}}

`istioctl install ` {{execute}}

`kubectl label namespace default istio-injection=enabled ` {{execute}}

Step 2 - First Example 

`kubectl run nginx --image=nginx ` {{execute}}

`kubectl get pods `{{execute}}

Step 3 - The Bookinfo Example 

`kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml ` {{execute}}

`kubectl get services `{{execute}}

`kubectl get pods `{{execute}}

`kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -sS productpage:9080/productpage | grep -o "<title>.*</title>" ` {{execute}}

Step 4 - Istio Gateway 

`cat samples/bookinfo/networking/bookinfo-gateway.yaml ` {{execute}}

`kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml ` {{execute}}

`kubectl get gateway ` {{execute}}

`export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}') ` {{execute}}
`export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}') ` {{execute}}
`export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}') ` {{execute}}
`export TCP_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="tcp")].port}') ` {{execute}}

`export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT ` {{execute}}

`curl -s "http://${GATEWAY_URL}/productpage" | grep -o "<title>.*</title>" ` {{execute}}

Step 5 - Istio Destination Rules 