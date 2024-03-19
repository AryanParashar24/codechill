---
title: "Istio⛵: Strengthening K8s with Service Mesh"
seoTitle: "Istio⛵: Strengthening K8s with Service Mesh"
seoDescription: "Istio is a powerful tool for reinforcing Kubernetes deployments with service mesh capabilities, positioned as a CNCF graduated project in 2023."
datePublished: Tue Mar 19 2024 19:24:10 GMT+0000 (Coordinated Universal Time)
cuid: cltyrjnr3000308kx2msfdnye
slug: istio-strengthening-k8s-with-service-mesh
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710876104584/9525fb9e-3822-4cec-858e-6f38a4c239e7.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1710876179718/ebfa9748-ae80-47bf-86f2-5a93fbd00e6b.png
tags: cloud, security, kubernetes, cloud-computing, devops

---

Istio is a powerful tool for reinforcing Kubernetes deployments with service mesh capabilities, positioned as a leading project within the Cloud Native Computing Foundation (CNCF). Istio plays a pivotal role in enhancing the resilience, observability, and security of microservices architectures. By seamlessly integrating with Kubernetes, Istio empowers developers and operators to manage complex networking tasks with ease, fostering efficient communication and robust service-to-service interactions.

Istio officially became a graduated project of the Cloud Native Computing Foundation (CNCF). This signifies its maturity, industry adoption, and commitment to open-source development.

One of the major feature of Istio revolves around the Service Mesh, so let's try to understand Service Mesh thoroughly at the first hand and then get to know about the Istio architecture.

If you want to have a quick recap about Istio before heading to this detailed Blog than head on to my Youtube Channel:

%[https://www.youtube.com/watch?v=x4ZahG4VHQw&t=2s] 

## General Requirements during Deployments

For any microservice application, there are certain requirements expected from a network engineer and here are some of them with the help of an example.

![Example taken from IBM YT channel](https://cdn.hashnode.com/res/hashnode/image/upload/v1710831314906/633743a2-3bf8-4f68-9cb3-feb3311e526e.png align="center")

Here in this example, we have taken a UI microservice which is talking to the Catalog v1 and Catalog v2 which will then be talking with the Inventory. There are certain requirements that are expected to be fulfilled by their application infrastructure from their network engineers which are:

* **Connection**
    
* **Security**
    
* **Observe**
    
* **Control**
    

### Connection

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710850748953/5106c203-249b-4c98-b01f-9f848f7e8b98.png align="center")

Here there has to be nice connection set up between all the different parts of our pod in the cluster and set up a network configuration to trace out the route for the packets and requests. Here we can set up 2 different catalogs v1 and v2 to split the traffic in different ratio like 9:1 or 1:1 so that in case some security vulnerability broke our infrastructure than the whole case can be handled without any breakage of service providing to the customers.

Even in case of a new a update is launched of our application than we still need to receive many feedbacks form the users to develop our application to the perfect application according to our users' expectations. Thus, in this case we can divert some percentage of our total traffic to our newer version and then after working on our application according to the needs of our users we can destroy the older versions and set up replicas of our updates version and divert the remaining traffic to those microservices having updated version of our application. This process is called as **<mark>The Canary Deployment</mark>**.

Whenever a new microservice is added int he cluster then the information about it's service endpoint is configured for web server. Thus, we have this information added in the application deployment code.

### Security

To handle the security of our pod we can set up the Mutual TLS which will help in the encryption and decryption of our requests passing from one component to another part of our pod. This will ensure that no-third party would be able to get access to your information and request without your permission.

Pods and their components does have many permissions and firewalls in order to allow the request the interception with the components of our pod, but once we had cleared all the permissions and entered in the cluster, we can do whatever we want which is pretty dangerous for big companies and sectors related to banking, security and defense.

### Observe

Observing the traffic flow in the system brings out a lot of important updates, helps in identifying the bottlenecks to the infrastructure and helps in observing how our application is working and map out the alternative paths if required.

### Control

Bringing new features and functionalities for our services and application components including decisions like traffic splitting, catalogs reaction to certain requests, setting rules and conditions can bring the best product possible.

# Istio & Service Mesh update on this infra.

Service Mesh helps in creating a sidecar side to our microservices which can act as a gateway for the request entered inside the pod which further intercepts with the main component of our cluster after it passes all the policies and tests. Thus, Service Mesh helps in creating this huge network of Envoy Proxies next to each component of our cluster.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710853790325/f580f28e-18cd-4f8a-b620-4e64bdcc8c00.png align="center")

Istio helps in setting up the configuration between all the proxies in the network and routing them to the next proxy in the network until it reach to it's destination or requested part of the pod.

Istio extends Kubernetes using CRDs so to apply Kubernetes configuration we will write and deploy our .yaml files and apply Kuberentes which then later be received by <mark>Istio Galky</mark> component which validate the file and then forward it to <mark>Istio Pilot</mark> which will convert those files to envoy config files and got distributed to each one of the proxies.

In case, we wants to make policies and rules for proxies to run the check for each requests then we can use <mark>Istio Policy </mark> which will report with the <mark>Istio telemetry</mark> for all the responses accepted for our requests.

Then the <mark>Istio Citadel</mark> which is responsible for providing strong identity to each services in our system, it generally certifies and then rolls them out to each proxy on our cluster to set up the network and perform Mutual TLS for all the requests forwarded.

Logic is being moved outside of the control plane and into the proxies itself through the Istio Policy and Istio Telemetry to avoid the additional network hop to performance improvement.

* **Gateway & Virtual Service**
    

Each of these pods have a <mark>Gateway</mark> at the starting of our pod in the cluster which looks over all the incoming and outgoing HTTP/ TCP connection requests of our pod to act as a load balancer and helps in traffic splitting sitting at the edge of our mesh.

Just after the gateway comes our <mark>Virtual Service</mark> which is responsible for passing the requirement from gateway to the service. This one can also be loaded after the gateway or it can also be loaded in between the UI and catalog as directly from one service to another service.

# Importance of Service Mesh & Istio's responsibility

Developer's team responsible for handling of these different microservices will be able to configure other stuff to the cluster if the proper network of proxies and policies are designed for the cluster and our pod. This builds up a lot of burden on the network engineers and make them more busy with the network layer of the cluster for metrics, security and communication, adding up more complexity to each microservice thus, Service Mesh helps by extracting all the non-business logic out of the microservice and packs them into a side car application that handles all these logic acts as a small application as a third party application so that developers can focus on their core business and contribute in growing their organization. So the cluster operators can easily configure through a simple API without having to worry about how the logic being implemented.

With Service Mesh we won't have to add their side car configuration as they would be added automatically in every microservice.

# Istio d Control Plane

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710875219369/0b812f93-087c-46e8-b680-1e2abd226530.png align="center")

Now, these seperate Istio Galky, Istio Pilot and Istio Citadel parts were a part of the traditional Istio Architecture which was later came together to form the Istio Control plane making it much easier for developers to Configure Discover and develop Certificates.

Istio integrates with popular orchestration platforms like Kubernetes, making deployment and management seamless. The Istio project offers various tools and extensions for monitoring, debugging, and managing the service mesh.

# Istio Day at KubeCon

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710875513050/39c2bfa0-efd4-44f0-b66f-23394e129da5.png align="center")

Istio Day community event for the industry’s most popular service mesh, where you will find lessons learned from running Istio in production, hands-on experiences, and featuring maintainers from across the Istio ecosystem.

After archiving their Open Service Mesh project, Microsoft has joined the Istio community for collaboration. This strengthens Istio's position as a leading service mesh solution.

Here's the link to view the schedule about the event on 19th March 2024:

%[https://colocatedeventseu2024.sched.com/overview/type/Istio+Day] 

Hope you get to know something new about the Service Mesh and Istio. Soon, I will be releasing more Service Mesh services like the Kuma by Kong and all the other CNCF projects which are holding their events on the 19th March 2024 at KubeCon, Paris.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710875811102/51348217-ded3-4d3b-855e-3e8585d0314d.jpeg align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)