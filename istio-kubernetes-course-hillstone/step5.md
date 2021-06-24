Istio Gateway.

## Task

`cat samples/bookinfo/networking/bookinfo-gateway.yaml`{{execute}}

`kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml`{{execute}}

`kubectl get gateway`{{execute}}

`export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')`{{execute}}

`export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')`{{execute}}

`export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}')`{{execute}}

`export TCP_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="tcp")].port}')`{{execute}}

`export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT`{{execute}}

`curl -s "http://${GATEWAY_URL}/productpage" | grep -o "<title>.*</title>"`{{execute}}
