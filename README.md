# kubernetes-pod-ip-finder
Simple Kubernetes Microservice to find all the IP addresses of Pods that have a set of labels. Exposes a simple REST API.

### Prerquisties

This Docker image needs to be run in a Kubernetes Cluster. You need to first create a Kubernetes Cluster and set up the ```kubectl``` tool. See the [guide](http://kubernetes.io/gettingstarted/) to learn how to create and configure a cluster.

Download the [controller.yaml](controller.yaml) and [service.yaml](service.yaml) files to install the service in your cluster.

### How to Use

1. Launch Service
   - ```kubectl create -f service.yaml```
1. Launch Controller
   - ```kubectl create -f controller.yaml```
1. To find all Pod IP addresses
   - ```http://kubernetes-pod-ip-finder/```
1. To find all Pod IP addresses with the label: "env: test"
   - ```http://kubernetes-pod-ip-finder/?env=test```
1. To find all Pod IP addresses with the labels: "env: test" and "role: database"
   - ```http://kubernetes-pod-ip-finder/?env=test&role=database```
1. The service will return an Array of IP addresses that match the labels
   - ```["10.168.9.14","10.168.3.27"]```


Note: This is not an official Google product
