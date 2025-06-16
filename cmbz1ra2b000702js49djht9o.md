---
title: "Cilium Egress Gateway: Secure API Integration"
seoTitle: "Cilium Egress Gateway: Secure API Integration"
seoDescription: "Discover the power of Cilium Egress Gateway API for improved security and dynamic connectivity in Kubernetes with eBPF-based kernel implementation"
datePublished: Mon Jun 16 2025 12:04:44 GMT+0000 (Coordinated Universal Time)
cuid: cmbz1ra2b000702js49djht9o
slug: cilium-egress-gateway-secure-api-integration
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1750075335926/39c94c7c-8869-446e-a2b9-fe341a50a5d5.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1750075412502/506adff8-6b2b-4f96-b121-5f58fdc56b32.png
tags: cloud, software-development, security, backend, computer-science, cloud-computing, devops, software-engineering, networking, cncf, cloud-native, cloud-security

---

Kubernetes changed networking over pods and namespaces which was just limited to routing and security between the application which was controlled by pod networks using Network Policies.

<mark>Cilium implements egress control at </mark> **<mark>Layer 3/4</mark>**<mark>, directly in the </mark> **<mark>Linux kernel using eBPF</mark>**

With Many solutions implemented, external connectivity tries to communicate with workloads living outside the Kubernetes Cluster which gets subjected to connectivity constraints and security enforcements.

Traditional Firewalling usually relies on static IP Addresses, although in case of Kubernetes and Cloud workload we might also need to manage connectivity & Traffic management with Dynamic IPs, which can be managed by Cilium Egress Gateway API and combination of some other Spacemaker solutions or Cloud-Native Solution Projects.

These traditional firewalling methods can make it really difficult to integrate a Kubernetes Cluster which has a varying and at the same time a dynamic number of nodes into such a network.

# Cilium Egress Gateway API

Cilium Egress Gateway API solve these all problems by specifying which nodes should be used by any particular pod in order to reach outside world.

Traffic from these pods will be Source NATed to IP address of the node and will reach the external firewall with a predictable IP, enabling firewall to enforce right policy on a specific pod.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1749968684365/c8a635b8-a454-4057-8e47-42dab97c7c49.png?auto=compress,format&format=webp align="left")

In contrast to other Egress or Gateway API solutions, a Cilium Egress Gateway API:

* Requires Cilium kube-proxy replacement
    
* Enables connectivity between Kubernetes Cluster and traditional Firewall.
    

## Benefits of using Cilium Egress Gateway API

Cilium implements egress control at **Layer 3/4**, directly in the **Linux kernel using eBPF**, offering:

1. **Policy-based egress routing**: You can define egress policies that route traffic **based on pod labels, destination CIDRs**, and even IP pools.
    
2. **IP Pooling**: Assigns dynamic or static public egress IPs per node or pod group.
    
3. **Node-aware policies**: You can ensure traffic is routed through a specific node with a public IP.
    
4. **Failover support**: If a node becomes unavailable, Cilium can reroute via another gateway dynamically.
    
5. **No sidecar, no proxy overhead**: Much lower latency and CPU usage.
    
6. **Integration with Gateway API (in progress/alpha)**: Brings declarative Kubernetes-native way of managing egress at CNI level.
    

# Implementing Cilium Egress Gateway API

Here’s an example which, we can also find from the official example given by the Cilium and Isovalent.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1749972552895/d605b2bb-a608-420f-8654-26f436bee98c.png?auto=compress,format&format=webp align="left")

Lets say we had 4 nodes as kind-worker, kind-worker2, kind-worker3, kind-worker4 with the 3rd and 4th node been planned to be deployed as Egress GatewayAPI. Now to handle the Egress Gateway functioning, we will carry out the following practices:

* Now as discussed for choosing which node to get deployed/bound with a pod for handling traffic, we’ll taint them from mistakenly scheduling any general-purpose pods.
    
    **Copy**
    
    ```bash
      kubectl taint node kind-worker3 egress-gw:NoSchedule
      kubectl taint node kind-worker4 egress-gw:NoSchedule
    ```
    
* Label them for better monitoring and observability.
    
    **Copy**
    
    ```bash
      kubectl label nodes kind-worker3 egress-gw=true
      kubectl label nodes kind-worker4 egress-gw=true
    ```
    
* All the kind nodes are attached to Docker network called `kind` (Kubernetes in Docker) which use 172.18.0.0/16 IPV4 CIDR.
    
    **Copy**
    
    ```bash
      docker network inspect -f '{{range.IPAM.Config}}{{.Subnet}}, {{end}}' kind
    ```
    
    * `CIDR` is Classless Inter Domain Routing Method for allocating IP address on the internet, designed to improve efficiency and manage growth of internet’s routing table.
        
* Add a new Dummy interface eth0 to both the kind-workers 3 & 4 with new address 172.18.0.42/16 and then add it to kind-worker 3 and 4 who’s IPs will be used by Cilium.
    
    **Copy**
    
    ```bash
      docker exec kind-worker3 ip link add net0 type dummy
      docker exec kind-worker3 ip a add 172.18.0.42/16 dev net0
      docker exec kind-worker3 ip link set net0 up
    ```
    
    **Copy**
    
    ```bash
      docker exec kind-worker4 ip link add net0 type dummy
      docker exec kind-worker4 ip a add 172.18.0.43/16 dev net0
      docker exec kind-worker4 ip link set net0 up
    ```
    
* Add Cilium and Egress Gateway API, disable Layer 7 proxy as its incomplete with Egress Gateway and attach two network interfaces to Egress Nodes called eth0 and net0.
    
    **Copy**
    
    ```bash
      cilium install \
        --version 1.17.1 \
        --set kubeProxyReplacement=true \
        --set egressGateway.enabled=true \
        --set bpf.masquerade=true \
        --set l7Proxy=false \
        --set devices="{eth+,net+}"
    ```
    
* Verify also that Cilium was started with the Egress Gateway feature:
    
    **Copy**
    
    ```bash
      cilium config view | grep egress-gateway
    ```
    

## Setting up Egress Server and Egress Policies

Needs to be attached to `kind` network, and we will pass the allowed source IP addresses as environment variables:

**Copy**

```bash
docker run -d \
  --name remote-outpost \
  --network kind \
  -e ALLOWED_IP=172.18.0.42,172.18.0.43 \
   quay.io/isovalent-dev/egressgw-whatismyip:latest
```

Retrieve the container's IP in a variable:

**Copy**

```bash
OUTPOST=$(docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' remote-outpost)
echo $OUTPOST
```

* Now lets deploy two more pods in our external outpost and see if they responds according to the labels we attached to them:
    
    **Copy**
    
    ```bash
      kubectl run tiefighter \
        --labels "org=empire,class=tiefighter" \
        --image docker.io/tgraf/netperf
      kubectl run xwing \
        --labels "org=alliance,class=xwing" \
        --image docker.io/tgraf/netperf
    ```
    
* Now we will add a Gateway Policies `egress-gw-policy.yaml` to route traffic to the external workload running in the network.
    
    * Resource to specify Cilium which Egress needs to be used for the traffci we’ll use: `CiliumEgressGatewayPolicy`
        
    * This will allow traffic to flow through one of the two Egress Nodes i.e. `kind-worker3` or `kind-worker4` .
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1749991486831/3f81956e-7bad-4166-8dcc-0e00495b9728.png?auto=compress,format&format=webp align="left")
        
        Here’s the `egress-gw-policy.yaml` file defined:
        

**Copy**

```bash
apiVersion: cilium.io/v2
kind: CiliumEgressGatewayPolicy
metadata:
  name: outpost
spec:
  destinationCIDRs:
  - "172.18.0.0/16"
  selectors:
  - podSelector:
      matchLabels:
        org: alliance
  egressGateway:
    nodeSelector:
      matchLabels:
        egress-gw: 'true'
    interface: net0
```

Then deploy the definition file it to the workload:

**Copy**

```bash
kubectl apply -f egress-gw-policy.yaml
```

If we try to deploy another pod with a new IP address with the org=alliance, then it will be accepted as it accepts the definition file policies.

**Copy**

```bash
kubectl run ywing \
  --labels "org=alliance,class=ywing" \
  --image docker.io/tgraf/netperf
```

## Accessing the external outpost server from the pods deployed

**Copy**

```bash
kubectl exec -ti xwing -- \
  curl --max-time 2 http://172.18.0.7:8000
kubectl exec -ti tiefighter -- \
  curl --max-time 2 http://172.18.0.7:8000
kubectl exec -ti ywing -- \
  curl --max-time 2 http://172.18.0.7:8000
```

1. Here since the traffic exits through one of the first two IP addresses been listed thatswhy, this command will give a success result for one amongst the first 2 of the IP address.
    
2. It will also give a success message with the 3rd IP address because it has org=alliance which matches with the policies been listed in the definition file for the Egress GatewayAPI.
    

Access the outpost from the X-Wing a few times in a loop:

**Copy**

```bash
for i in $(seq 1 10); do
  kubectl exec -ti xwing -- \
    curl --max-time 2 http://172.18.0.7:8000
done
```

Note that traffic always exits the cluster from the same IP address, which means it always uses the same exit node.

In Cilium OSS, Egress Gateway Policies are used to select a node for a traffic, and that node will always be used for that given traffic.

For Managing the IP through which our traffic can exit, we will need to use High Availability type while defining our Cilium Egress Gateway API.

Soon, I will be uploading another Blog on High Availability in Cilium Egress Gateway API and will also integrate other CloudNative Solutions like kube-vip, etc. Till then stay excited:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1750049728590/417485cc-1686-47a6-9fba-bdfb7590b1d8.gif?auto=format,compress&gif-q=60&format=webm align="left")

If you like my Article then please react to it and connect with me on Linkedin & Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Linkedin: [**aryanparashar/**](https://www.linkedin.com/in/aryanparashar/)

My Twitter Profile: [**Aryan\_2407**](https://twitter.com/Aryan_2407)

My Youtube:

[**https://www.youtube.com/@AryanParashar\_**](https://www.youtube.com/@AryanParashar_)