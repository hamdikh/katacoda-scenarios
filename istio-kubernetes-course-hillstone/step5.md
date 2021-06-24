Istio Gateway.

## Task

Hmmm there is a gateway, let's inspect this file 

`cat samples/bookinfo/networking/bookinfo-gateway.yaml`{{execute}}

Once inspected, let us try and apply it

`kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml`{{execute}}

Let us verify our gateway

`kubectl get gateway`{{execute}}

Next we'll be doing some **_MOJO JOJO_** to be able to test our application

`export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')`{{execute}}

`export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')`{{execute}}

`export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}')`{{execute}}

`export TCP_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="tcp")].port}')`{{execute}}

`export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT`{{execute}}

One all the command above are executed, you can curl to see if you can access the product service

`curl -s "http://${GATEWAY_URL}/productpage" | grep -o "<title>.*</title>"`{{execute}}

WOW ! seems better ! but how come ?
