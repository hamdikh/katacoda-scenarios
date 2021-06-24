This is your first step.

## Task

First of all we need to configure our _kubernetes_ environment so all you need to do is launch a **command**

`launch.sh `{{execute}}

Once this is done, you need to verify the kubernetes _installation_ please type the following **command**

`kubectl get node `{{execute}}


`curl -L https://istio.io/downloadIstio | sh -`{{execute}}


`cd istio-1.10.1 && export PATH=$PWD/bin:$PATH `{{execute}}

`istioctl install --set profile=demo –y`{{execute}}

`kubectl label namespace default istio-injection=enabled`{{execute}}

