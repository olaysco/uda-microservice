[![Build Status](https://www.travis-ci.com/olaysco/uda-microservice.svg?branch=master)](https://www.travis-ci.com/olaysco/uda-microservice)

Each of the service i.e. the User Service, Feed Service and Frontend are separated into differnet folder with their respective deployment.yaml and service.yaml file hence each of the service exisitng in a separate pod within the cluster, for this size of project there's no immediate advantage of having each of the service in separated pods as they can efficiently exist within a single k8s cluster pod sharing the same dns and enabling communications with different ports.
The advantage of this approach are
- It gives us a logical idea of how each serivce in a microservice architecture are usually handled by different software teams and most times each service exists in different repository.
- Should a pod fail, or there's a need to restart a pod for update or maintenace it would only affect the service in that pod and not all the pods in the cluster
- Helps to enforce the one process per container principle
- Individual horizontal scaling of each of the service as per computation and traffic needs (saves cost).
- No perfect software, there would always be need to debug a service in production, with each of the service in their pod I can easily inspect the logs and know where the fault is.

![Architecture rough sketch](https://images.unsplash.com/photo-1612021595824-0194cdb0e996?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80)
