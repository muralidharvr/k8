## Configuration of "Hello World Service"  program on Ingress Controller on Linux

### Prerequisite
####  &emsp;  1. Kubernetes cluster (atleast the control plan is installed on Linux and is up and running)
####  &emsp;  2. MetalLb - load balancer is configured and up and running
####  &emsp;  3. Ingress Controller is configured and up and running.



### Following are the steps:
#### 1. Create new namespace "hwns"
#### &emsp; sudo kubectl apply -f 01-hello-world-namespace.yaml
#### 2. Create Hello World Service
#### &emsp; sudo kubectl apply -f 02-hello-world-service.yaml
#### 3. Create Hello World Deployment 
#### &emsp; sudo kubectl apply -f 03-hello-world-deployment.yaml
#### 4. Create Hello World Ingress Configuration
#### &emsp; sudo kubectl apply -f 04-hello-world-ingress.yaml

### Debugging Commands:
#### 1. To view all the resource under the namespace "hwns"
#### &emsp; kubectl get all -n hwns
#### 2. To view all the ingress resources 
#### &emsp; kubectl get ingress --all-namespaces
#### 3. To view the list ingress rule configured for the hello world ingress 
#### &emsp; kubectl describe ingress hello-world-ingress -n hwns
#### 4. To check the traffic to the load balancer
#### &emsp; sudo tcpdump -i any host 192.168.1.151 (where 192.168.1.151 is the IP of Load Balancer)
#### 5. To view the last 50 log for in the ingress pod
#### &emsp; kubectl logs <pod name> -n <namespace> –tail 50 
