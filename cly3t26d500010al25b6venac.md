---
title: "Cilium Gateway API: Bridging Networks Beyond Envoy Proxies"
seoTitle: "Cilium Gateway API: Bridging Networks Beyond Envoy Proxies"
seoDescription: "Article explores the Cilium Gateway API a CuttingEdge solution that goes beyond traditional Envoy proxies with better performance, security & flexibility"
datePublished: Tue Jul 02 2024 02:44:14 GMT+0000 (Coordinated Universal Time)
cuid: cly3t26d500010al25b6venac
slug: cilium-gateway-api-bridging-networks-beyond-envoy-proxies
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719853568706/f5ff8771-eb7b-41e9-a364-f78fd626c1b6.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1719888083889/5bd2c411-fe02-4c78-b66c-7e7ac63517e5.jpeg
tags: cloud, security, kubernetes, cloud-computing, devops, ebpf

---

In the ever-evolving landscape of Kubernetes and cloud-native architectures, network security and efficiency have become paramount. This article explores the Cilium Gateway API, a cutting-edge solution that goes beyond the traditional Envoy proxies, to deliver enhanced performance, security, and flexibility.

Cilium is a successfully graduated project by Cloud Native Foundation which is responsible for building many such amazing project under Isovalent which are evolving the whole Cloud Native & DevOps world by higher Security, Sustainability and Integrations.

## Embedded Envoy Proxies

Cilium already uses Envoy for Layer7 (L7) policy and observability for some protocols and this same component is used as a sidecar in many popular Service Mesh implementations.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719819348254/49c26782-da2f-4dbc-b1ae-1cc2f9df2813.png align="center")

So, it's natural to extend Cilium to offer more of features commonly associated with Service Mesh. Instead this Envoy is embedded with Cilium Cluster meaning only one Envoy container is required per node.

## eBPF Application

In a typical Service Mesh, all network packets need to pass through a sidecar proxy container on their path to or from application container in a Pod.

So every packet traverse TCP/IP stack three times before even leaving the Pod.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719823326259/1e22b4b0-862a-40f7-8228-b13f91a59dc0.png align="center")

In Cilium Service Mesh, proxy container are moved top host and kernel so that sidecars for each application pod aren't required as eBPF allows to intercept packets at sockets as well as network interface, Cilium can drastically shorten overall path for each packet.

* **If you don't know about Service Mesh then here is it...**
    

Service Mesh is a technology to provide community between the services along with other functionalities like observability, security, traffic management and resilience which are :

1. Resilient Connectivity:
    
    Service-to-Service connectivity across boundaries such as clouds, clusters and premises. Communication must be resilient and fault tolerant.
    
2. L7 traffic management:
    
    Load balancing, rate limiting and resiliency must be L7 aware (HTTP, REST, gRPC, Web Socket...)
    
3. Identity-based Security:
    
    Authenticating sender and receiving services based on identities instead of a network identifier.
    
4. Observability and Tracing:
    
    Observability in the form of tracing and metrics is critical to understanding, monitoring and troubleshooting application stability.
    
5. Transparency:
    
    The function must be available in transparent manner i.e. without required to change application code.
    

* Now for the general usability for any random application if we wish to use Service Mesh with traditional practices where our application was being written in different languages like C, Java, Python, Golang, Rust **then we need to modify our applications**.
    
* Even in the worst cases we were using different libraries of these specific languages then **we need to use different Service Mesh libraries for every language framework which are required for handling our application being written in different libraries.**
    

Thatswhy, a Sidecar model was introduced which essentially moved the mesh library into a sidecar. Thus we no longer need to use a language specific library but we could actually use a sidecar proxy and keep our application unmodified. Thus the conversation and managing of the application which has been coded in some other language goes in the below format to get converted to some other language.

<table><tbody><tr><td colspan="1" rowspan="1"><p>Python App</p></td><td colspan="1" rowspan="1"><p>Sidecar Proxy (Mesh Library)</p></td><td colspan="1" rowspan="1"><p>Sidecar Proxy (Mesh Library)</p></td><td colspan="1" rowspan="1"><p>Go App</p></td><td colspan="1" rowspan="1"><p></p></td><td colspan="1" rowspan="1"><p></p></td><td colspan="1" rowspan="1"><p></p></td></tr></tbody></table>

So Cilium have been trying to avoid sidecar proxies for every service, resource created in the pod. Although they are with the proxies idea but not for every pod instead **<mark>Cilium is with running one proxy per pod or one per Namespace.</mark>**

Cilium does have Service Mesh integration from starting and now have been making efforts to make Service Mesh as a built-in part of operating system and be transparently available without needing to run additional sidecar process.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719839555130/f4e175c0-dfd9-4374-a4e6-599654527633.png align="center")

This means that from an integration perspective it will look like:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719842311495/30c42d4a-811c-4ce5-8b8f-fcddd3fe8627.jpeg align="center")

So will have a Service Mesh sitting as a part of our Network stack in our operating system, above TCP/IP (TCP/IP are often kind of a Old School Service Mesh with security feature).

Service Mesh is also similar to it with many new features being added to increase efficiency, security, observability, integrations and adopted Microservices Technology into Cloud Native infrastructure.

## Why to get rid of Sidecar ?

Sidecars are expensive to inject in parallel with all pods, resources, namespaces and services.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719840414846/8128ea28-79ea-4866-baee-322d8b0a962f.png align="center")

So here is the way how a proxy is injected separately as a user proxy so we haev to do this via transparent network injection and have to pass through network stack multiple times which Costs High!!

If we would look at the Latency rates:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719842580864/1f08dbcc-a9a7-419d-bbb3-85edefd9455e.png align="center")

Proxy-based visibility is pretty High which provides a L7 visibility and the baseline says no visibility of latency at 10k HTTP requests. The eBPF-based visibility is very low comparatively which is used with open Telemetry for tracing data.

## Memory & Footprints

Number of Services running with Sidecar model will double then before, thus engaging and using double the number of computation than before. For example: if there were 30 services running earlier then, now the number of services running after having the sidecars being latched with the original ones will increase the number to 60 and thus the extra computational power will also be harmful for the environment, reducing sustainability due to extra footprints being produced.

# Practices

The installer will attempt to automatically pick the best configuration options for you. Please see the other tabs for distribution/platform specific instructions which also list the ideal default configuration for particular platforms.

```bash
cilium install --version 1.15.6
```

To Install Cilium into the Kubernetes cluster pointed to by your current kubectl context.

```bash
cilium status --wait
```

To view if Cilium is installed perfectly which will wait for Cilium to be Up & Running, or report it's status. This command will show the following line:

```bash
$ cilium status --wait
   /¯¯\
/¯¯\__/¯¯\    Cilium:         OK
\__/¯¯\__/    Operator:       OK
/¯¯\__/¯¯\    Hubble:         disabled
\__/¯¯\__/    ClusterMesh:    disabled
   \__/

DaemonSet         cilium             Desired: 2, Ready: 2/2, Available: 2/2
Deployment        cilium-operator    Desired: 2, Ready: 2/2, Available: 2/2
Containers:       cilium-operator    Running: 2
                  cilium             Running: 2
Image versions    cilium             quay.io/cilium/cilium:v1.9.5: 2
                  cilium-operator    quay.io/cilium/operator-generic:v1.9.5: 2
```

Run the following command to validate that your cluster has proper network connectivity:

```bash
cilium connectivity test
```

which will be showing the following lines as:

```bash
$ cilium connectivity test
ℹ️  Monitor aggregation detected, will skip some flow validation steps
✨ [k8s-cluster] Creating namespace for connectivity check...
(...)
---------------------------------------------------------------------------------------------------------------------
📋 Test Report
---------------------------------------------------------------------------------------------------------------------
✅ 69/69 tests successful (0 warnings)
```

### Gateway Class

If CRDs have been deployed before and a Gateway Class will be deployed by Cilium during its installation.

```bash
kubectl get GatewayClass
```

To certify if the Gateway Class has been installed already by the Cilium and eBPF.

This is to let infrastructure providers offer different types of gateway users to choose the type of Gateway which suits their infrastructure best. There are majorly 2 types of Gateway Classes that can be deployed:

1. Internet Gateway Class: For Internet facing
    
2. Private Gateway Class: For private and internal application
    

Gateway APIs have various types of APIs. When using Ingress, all functionalities were defined in one API. By constructing ingress routing required into multiple APIs users benefit from a more generic, flexible and route-oriented model.

By constructing ingress routing required into multiple APIs users benefits from a more generic, flexible and role-oriented model.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719856593980/4e9da80a-e6e6-4abf-b495-3d982b7a4a92.png align="center")

A modern set of PAIs for developing L4 and L7 routing in Kubernetes which are different level of OSI models:

**L4 Routing:**

It is done by a load balancer deals with transparent layer protocols like TCP and UDP.

**L7 Routing:**

L7 routing handled by a reverse proxy like NGINX works with application layer protocols like HTTP, HTTPS and HTTP/2 allowing for more granular traffic control based on application specific data.

Cilium's own Load Balancer provide IP add management (IPAM) and Layer 2 announcement of IP address assigned to Load Balancer serviced.

#### Benefits of Using Cilium Load Balancer

* **Enhanced Performance**: Leveraging eBPF, Cilium operates efficiently with minimal overhead.
    
* **Improved Security**: Integrated network policies and security features help in protecting containerized applications.
    
* **Scalability**: Efficient IP address management and load balancing algorithms support large-scale deployments.
    
* **Seamless Kubernetes Integration**: Works seamlessly with Kubernetes, making it easy to deploy and manage.
    

#### Use Cases

* **Microservices Applications**: Optimizes traffic distribution and enhances the performance of microservices applications.
    
* **High-Availability Systems**: Ensures continuous availability of services by effectively managing IP addresses and load balancing.
    
* **Secure Cloud-Native Environments**: Provides security and observability features to monitor and protect cloud-native applications.
    

I have also written a detailed blog on **<mark>Cilium, eBPF and Isavalent</mark>** other projects which was highly loved by all of you guys😄. So in case you want to learn more about them then have a look at my blog below:

%[https://codechill.hashnode.dev/cilium-next-generation-networking-security-of-cncf-with-golang-ebpf-hubble] 

Also, eBPF is goin to organize an event on 11th September so don't forget to grab you Virtual seats at the event 😄 : [https://ebpf.io/summit-2024/](https://ebpf.io/summit-2024/)

Soon I will be releasing more detailed and more described blogs on Cilium, eBPF and similar kind of really important tech like Kafka, WASM, AI-LLM collaborations and many other important topics, frameworks and projects which can create an impulsive effect on our developing cycle and security.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719887818240/9e5d4e96-6e29-4018-a548-b9701265c459.gif align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)

My Youtube:

%[https://www.youtube.com/channel/UCPukGLZnjiMnPdDOFwZWV_A]