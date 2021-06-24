Install Istio.

## Task

Let's download istio and install it on our cluster 

`curl -L https://istio.io/downloadIstio | sh -`{{execute}}

Once downloaded, we will need to add istio directory to the PATH environment variable

`cd istio-1.10.1 && export PATH=$PWD/bin:$PATH`{{execute}}

Yay ! _istioctl_ is not available for use, let's see what can we do with it !

`istioctl install`{{execute}}

**don't forget to type _y_ otherwhise istio won't be installed** 

WOW ! that was quick ! 

Let us now configure our namespace to use istio

`kubectl label namespace default istio-injection=enabled`{{execute}}
