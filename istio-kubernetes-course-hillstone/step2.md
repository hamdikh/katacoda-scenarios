Install Istio.

## Task

`curl -L https://istio.io/downloadIstio | sh -`{{execute}}

`cd istio-1.10.1 && export PATH=$PWD/bin:$PATH`{{execute}}

`istioctl install`{{execute}}

`kubectl label namespace default istio-injection=enabled`{{execute}}
