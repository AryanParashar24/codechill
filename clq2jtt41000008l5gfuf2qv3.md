---
title: "How Cloud Infrastructure is Important  ₿"
seoTitle: "How Cloud Infrastructure is Important  ₿"
seoDescription: "Get to know Why does the infrastructure planning is important & about diff. mechanisms & problems we get to see while planning our application architecture"
datePublished: Tue Dec 12 2023 16:20:22 GMT+0000 (Coordinated Universal Time)
cuid: clq2jtt41000008l5gfuf2qv3
slug: how-cloud-infrastructure-is-important
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702054103432/e5ec4928-0ce6-418a-8407-e7b5f32c278a.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1702397466470/6b97f372-e6e8-4571-bfc0-eb6a867e0a06.jpeg
tags: cloud, software-development, software-architecture, kubernetes, cloud-computing, devops, software-engineering, wemakedevs

---

In this Blog, we will get to know why the Infrastructure planning of our application is one of the most important tasks by getting to know about the different mechanisms and problems faced during its development.

We have heard everyone worrying about the infrastructure and the architecture of their systems, onto the different positions like public clouds, private or any other medium. Many new services, platforms and ideas have come onto the main stage to solve these problems and make these processes more frictionless and smooth as possible, to make our application easy to collaborate with different platforms, frameworks and services with lesser effort.

Let's try to understand why these all measures are taking place in the domain of designing a nice infrastructure for the application and performing tasks seamlessly, collaborating with different services and dependencies.

# Landscape

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702281644308/9e161c2a-d9e1-4e26-a30b-cefce1090385.png align="center")

This Landscape of cluster management systems is formed up of various services offering general functionalities along with their extended features which makes them stand out from the other services in the landscape, attracting teams/ users from various professional backgrounds depending on their usage of applications.

# Open Source Initiative

## Introduction

The Open Source Initiative (OSI), established in 1998 by Eric S. Raymond and Bruce Perens, is a non-profit organization dedicated to championing and safeguarding the principles of open-source software. At its core, OSI advocates for transparency, collaboration, and the unrestricted sharing of software source code. One of its pivotal contributions is the formulation and maintenance of the Open Source Definition (OSD), a set of ten criteria that delineate what constitutes an open-source license.

**OCI Key Objectives:**

1. **Advocacy and Education:**
    
    * OSI serves as a key proponent, spreading awareness about the advantages of open-source methodologies.
        
    * It strives to educate individuals and organizations on the benefits of embracing open-source principles.
        
2. **License Approval:**
    
    * OSI plays a pivotal role in evaluating and approving open-source licenses based on their alignment with the OSD.
        
    * Approved licenses are cataloged and made available on the OSI website.
        

### Contribution

While OSI itself does not develop projects, it oversees the broader open-source community. Here are some major projects aligned with OSI principles:

1. **Linux:**
    
    * The iconic open-source operating system kernel is foundational to many Linux distributions.
        
2. **Apache HTTP Server:**
    
    * A widely used open-source web server software.
        
3. **Python:**
    
    * A versatile and powerful programming language with a thriving open-source community.
        
4. **Kubernetes (K8s):**
    
    * An orchestration platform for containerized applications, managing container deployment, and scaling.
        
5. **Cloud Native Computing Foundation (CNCF) Projects:**
    
    * CNCF, while a separate entity, hosts projects that align with OSI principles, including Kubernetes, Prometheus, and Envoy.
        

## Limitations

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702291437347/25863018-7e5f-4c7a-a127-65e9766900d8.png align="center")

Some limitations are generally observed for various open-source applications, based on which a particular service is being chosen which solves most of these problems in a much more efficient way.

### Simplicity

When it comes to Simplicity, we can observe how long it takes for the container to deploy the Kubernetes cluster, which could be minutes, hours or days. For example, while we are deploying a cluster through the virtual machine which would possibly some minutes, for more customized environments like the physical services might take up one or more days as well.

### Admin or Operator Access

We might have some admin or access problems as well while working with the services. For example, you don't want to use etcd as the database but you want to move to postgress which is possible for many services in the landscape but, might not be possible for some other services of the landscape.

### Cost optimization and Zero Lockin

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702397128033/dac9d80c-8102-4176-ab88-843353c93c71.gif align="center")

#### <mark>Cost Optimization</mark>

Cost optimization is one of the key features, which is the ability to minimize expenses associated with software development, deployment, and maintenance. Open-source software is typically distributed freely, eliminating licensing fees. Organizations can leverage and modify the source code without incurring additional costs.

#### <mark>Zero Lockin</mark>

Zero lock-in is a principle emphasizing the absence of vendor lock-in. In the open-source realm, this means users are not tied to a specific vendor or technology stack. It promotes interoperability and the freedom to migrate between different solutions without significant challenges. However, it isn't common to all the services, some of them have solutions, made to lock you. For example, easy to move applications from a cluster running in AWS like EKS towards a cluster running in Azure AKS, while not possible to perform with all the services within the landscape.

### True Multi-Cloud for Apps Mobility

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702397250402/27ca32d5-e005-4583-944c-d5a5d42e701e.gif align="center")

Building an application and then deploying it on different cloud architectures is an important choice to make, depending on our needs and services.

#### **<mark>Infrastructure</mark>**

There are various cloud environments in which we can choose to manage and deploy our applications, such as Public cloud, Private cloud, Bare metals, Virtual Machines and Air-Gapped.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702319565678/8cf51182-b5a4-4d9b-8a3e-9ea383e83c13.png align="center")

##### <mark>Public Clouds</mark>

Public Clouds are the same as the Virtual Machines, where we will be able to host our Kubernetes clusters across different regions of public clouds.

##### <mark>Bare Metal</mark>

These are another environment for uploading our Kubernetes clusters for use cases where we may have to include AI/ ML applications or functionalities to manage the usability of GUI or multi-cores. We would also be able to use Kubernetes on top of our clusters at scale on top of Bare metal.

##### <mark>Virtual Machines</mark>

Virtual Machines are another host for our Kubernetes clusters which can be used for public or private clouds based on our requirements, which is also something we want to leverage.

##### <mark>Edge</mark>

The edge architecture environment in infrastructure refers to the distributed computing model where computing resources are brought closer to the data source or endpoint devices. This is in contrast to the traditional centralized cloud computing model. In edge computing, processing and storage capabilities are placed near the "edge" of the network, closer to where data is generated.

##### <mark>Air-Gapped</mark>

An "air-gapped" environment refers to a system or network that is physically isolated from external networks, including the Internet. The term "air gap" implies that there is a literal gap of air between the isolated system and other networks, preventing any direct communication.

Many of the services we discussed earlier, might not have allowed the mixture of these services and the management of Kubernetes of Kubernetes to all of these environments at the same time simultaneously.

#### <mark>Status of Infrastructure &amp; specs</mark>

To deploy a solution on top of multiple availability zones, we will need at least 3 physical sites within a range of 10-20 km range to reduce the latency rate by 10 milliseconds latencies.

You don't need to deploy your clusters across all sites, we can have 2 for deploying clusters and one for forums, or all 3 for deploying different entities, you will have your management cluster across different data centers.

In our management clusters, we can have 3 clusters or 3 nodes for database management where we can have let's say 2 active and 1 for Quorum sites.

**<mark>Quorum Site:</mark>**

Quorum sites refer to site or cluster that plays a crucial role in achieving consciousness or quorum among distributed components. It is a concept used to ensure the majority of nodes agree on a particular decision or state before proceeding which helps in data consistency and site reliability even in times of a network partition or node failure.

The main reasons for choosing these two nodes as active and ono eas quorum are:

1. <mark>High Availability:</mark> If one node fails then the other can continue to operate and maintain the system. The quorum site determines which node is automatic.
    
2. <mark>Voting Mechanism:</mark> In distributed systems, each node has a vote. To make a decision, the majority is required and the quorum site acts as a majority decision in the case of a tie.
    
3. <mark>Data Consistency:</mark> Quorum-based system ensures data consistency by requiring the majority of nodes to agree on updates or changes before they are considered valid.
    

We can have specifically one, two or three clusters and have components like Cube Federation, to ensure the deployment of components or pods, across these different clusters. Once these are set up, this base setup you will be ready to start to host different Kubernetes clusters that will be managed by the management cluster, this is what we call a Tri Cluster.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702382547798/ef335efc-e5ea-4829-af5a-010b4f4cca83.png align="center")

Here is an example, we have a single cluster spread across 3 nodes where dc1 and dc2 are used to deploy Tri Cluster.

dc1 and dc2 are used to deploy in Tri Cluster and these are running in Virtual Machines. Once we have it for one single region then we can replicate it for multiple other regions as well. In this way, the pattern of one region can be replicated for another region as well.

### Bespoke

"Bespoke" refers to software that is custom-built for a specific purpose or tailored to meet specific requirements. It essentially means a solution that is crafted or designed for a particular use case.

Now, regarding the limitations of the open-source initiative, one limitation is that it may not always provide a "bespoke" solution. Open-source software is developed collaboratively, and while it can be highly customizable, it might not always perfectly align with the specific needs of an individual or organization. In some cases, businesses or projects may require highly specialized software that goes beyond the scope of what the broader open-source community is working on.

## Core Infrastructure services

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702396231029/bce29f11-7ef6-41ae-b5f1-bb34798caf3f.jpeg align="center")

Certain characteristics are always considered to be looked into while developing a proper Infrastructure for an application:

### Hard Muli-Tenancy

An important capability is due to security reasons for which we want to separate different users and resources, whether in a physical or a virtual environment.

So, the ability to create tenants and then manage dedicated compute storage and networking resources without having a way to have data migrated i.e. seen by other tenants inside one tenant is called Hard multi-tenancy and is key that allies with security principles. Apart from security, it can help in price monitoring and saving cost experience as it monitors the resources consumed at any infrastructural level, like how many CPUs, public IPs, nodes, resources and load balancers are we using at other Virtual Machines.

### Scalable Internal & External Networks

While building underlying or overlaying network infrastructure, you have modern infrastructure services that support box overlays.

We don't only need to manage underlays but we can scale them out with overlays (physical network infrastructure that provides the foundation of overlays networks), for example with VXLAN (Virtual Extensible Local Area Network).

We can manage our external network properly, you can have a dedicated external network or you have one single external network (internet) having all your customers connected. You can select the backend storage.

### Selection of Proper Storage Backend

We have various options to choose the environment for backend storage like local storage or Software-driven Storage like port works or Ceph, or applications like Fel storage so that you can continue deploying Kubernetes clusters and host database, which use local storage units for speed which might be in the form of NVMe disks(Non-Volatile Memory Express), which are connected to local servers and Kubernetes clusters will have volumes collected from local disks to provide high-speed access where performance is a critical factor in production.

Ceph is an Open Source storage platform designed for scalability, performance and reliability. It provides object storage, block storage and file storage in unified systems.

We can also consider having SDS (Software-driven Storage) to have a mixture of different backends to combine in Kubernetes and child-Kubernetes clusters.

### Local Balancers and Auxillary Services

Load Balancers are something, we can provide from the infrastructural layer depending on the environment, that we are currently using for our application. For example, we can leverage our elastic load balancers, if we are using AWS. If we don't have any solution provided by this underlying infrastructure, we can always use software load balancers like Metal lb, which is an Open Source project that provides a network load balancer implementation for bare metal Kubernetes clusters.

In Kubernetes, load balancers are used to distribute network traffic across multiple nodes in a cluster, ensuring efficient and reliable access to Service. However, in source on-premise or bare metal environments might not be enough to be available or suitable.

Metal lb fills this gap by offering solutions to load balancer environments where no external cloud provider offers native load balancer service. It allows you to expose service running in Kubernetes clusters to an external network and it can operate in either a layer 2 (data link) mode or layer 4 (transport layer) mode.

**<mark>Data Link Layer:</mark>**

**Function:** The data link layer is the second layer of the OSI (Open Systems Interconnection) model and is responsible for the reliable transmission of data frames between nodes over a physical link.

**<mark>Transport Layer:</mark>**

**Function:** The transport layer is the fourth layer of the OSI model and is responsible for end-to-end communication and data flow control between devices on a network.

If you want to leverage SSO then we would need to have an identity broker like Klob, to help you do SSO between your management cluster and your tri clusters, you will need to have a DNS resolver that will allow your service that will allow your services externally in an easier way than just using base IPSec Certificates so that you terminate TLS communication after we have built the underlying infrastructure.

  
**SSO**: Single Sign-On is an authentication process that allows a user to access multiple applications or services with a single set of login credentials. Once authenticated, the user can move between systems or services without the need to log in again.

**IPSec**: Internet Protocol Security. IPSec certificates are used for securing communication over IP networks. They are often employed to establish Virtual Private Networks (VPNs) for encrypted and authenticated communication between devices.

**Klob:** An identity broker like Klob is a service that facilitates SSO by managing authentication and authorization processes between multiple applications. It enables users to log in once and gain access to various connected services without the need to re-enter credentials.

Hope you got everything, you came here to know about and this blog would have been able to add some value to you. Soon, I will be posting some blogs discussing the Projects, offering better management of infrastructure, securing, and real-time monitoring of architectural components & resources like K0s & K0s motron.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702396957924/c4962bbc-1e7e-4189-ad96-266146a38786.gif align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)