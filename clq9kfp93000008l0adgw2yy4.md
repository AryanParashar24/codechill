---
title: "K0S - Zero-Friction Kubernetes"
seoTitle: "K0S - Zero-Friction Kubernetes"
seoDescription: "Here in this blog, we will be learning about one of the major lightweight Kubernetes distribution k0s developed by the Lens (Mirantis)"
datePublished: Sun Dec 17 2023 14:11:47 GMT+0000 (Coordinated Universal Time)
cuid: clq9kfp93000008l0adgw2yy4
slug: k0s-zero-friction-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702458038063/2e853808-06b0-411f-be3a-16ebdf62a1f4.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1702822142710/de58a4c4-4499-48d5-9128-52f655136a54.png
tags: cloud, software-development, kubernetes, cloud-computing, devops, hashnode

---

Here in this blog, we will be learning about one of the major lightweight Kubernetes distribution k0s developed by the Lens (Mirantis).

K0s is an [Open source](https://github.com/k0sproject/k0s) project and the successor of the [Pharos Kubernetes](https://k8spharos.dev/) distro that was also developed and maintained by the team. It is a streamlined, easy-to-install and versatile Kubernetes distribution developed by Lens, a part of Mirantis, which has gained prestigious CNCF Certification as a CNCF Certified cluster and Pips 140 certification, which is flexible and can run on any platform like a public cloud or private cloud, on hybrid, on-premise or multi-cloud whether it's on VMs, bare-metal servers.

k0s is a modern, 100% upstream vanilla Kubernetes(**a basic, open-source version of Kubernetes that is maintained by the Kubernetes community**) distro that is designed and packaged without compromise. It is broadly applicable from local development to large-scale production deployments. It runs anywhere and everywhere, with no dependencies, and 1 line installation.

For those who don't know about Kubernetes distributions, these are the packaged releases of Kubernetes, the Open Source container orchestrator. Kubernetes itself provides a set of core functionalities for container management, scaling and orchestration but a distribution includes Kubernetes along with additional tools, configuration and sometimes additional software for simple deployment, management and use.

## K0s Features Insights

K0s provides a Simplified and efficient way to deploy and manage Kubernetes clusters. With a focus on simplicity and flexibility, K0s streamlines the installation process making it accessible to a wide range of use cases from the development environment to production deployments.

With its modular and pluggable architecture, K0s empowers users to customize their Kubernetes deployment according to their specific needs. Whether you are a developer looking for a straightforward setup or all operator seeking and control, K0s offers a user-friendly solution for managing Kubernetes clusters with ease.

Once we are finished overlaying our infrastructure to the public cloud where our APIs are leveraged mainly or in private clouds, where we need to manage the physical layer on top of which of our virtualization layers & bare metals where again we have physical part then, edge and air gap where we have specific constraints like the selection of hardware at the edge and building local repo for the air-gapped environment.

Airgapepd environment is a network or system isolated from other external networks, specifically from the internet to enhance security by preventing unauthorized access or data exfiltration.

**The main reasons for its popularity include:**

* **Easy to install on Linux without additional software package**:
    
    k0s is known for its user-friendly installation process on Linux, requiring no additional software packages. This simplicity contributes to its widespread adoption.
    
* **K0s leverages Upstream Kubernetes**
    
    K0s Allow developers to create a distro that can run on any operating system and supports various higher-level services and solutions. K0s is also easier to maintain as all the core upstream Kubernetes components are self-contained, making the execution of modules easier at runtime.
    
* **Security vulnerabilities can be fixed directly in the k0s binary**:
    
    K0s is built as a single binary package of size (around 165 Mb), which means all the necessary libraries embed into a single self-extracting archive that is available to execute without any dependencies. Being a single binary k0s consists of core components, OS dependencies, and components packaged as a FIPS-compliant distribution for safe use in highly confidential testing environments.
    
* **k0s offers the advantage of independent upgrades** for the operating system (OS) and the k0s distribution. This flexibility allows users to update each component separately, ensuring a smooth and tailored upgrade process.
    
* **The control plane stays wholly isolated and is not directly a part of the cluster**:
    
    K0s decrease the chances of running typical workloads on controller nodes. K0s has no container runtime or kubelet running, creating a direct connection between the control plane and the cluster workers.
    
* **Kine for a Variety of Data Storage Backends**
    
    K0s embeds Kine, which enables MySQL, Postgres, and SQLite to manage and configure cluster data stores. Kine implements an etcd API, which translates etcd calls into the desired API for implementing endless storage architecture variations.
    
* **Lightweight Design for Edge Computing:**
    
    k0s's lightweight design is particularly advantageous for edge computing scenarios with limited resources. It is well-suited for deployment on edge devices and in Internet of Things (IoT) environments.
    

## History

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702821621015/38a6f45b-5bcf-4b05-9354-ff246f2401c6.gif align="center")

The deployment teams at Mirantis, including those working on the Lens IDE, sought to enhance the capabilities of Kubernetes (k8s) by introducing extensions. During this process, they recognized the need for an ultra-lightweight and versatile Kubernetes distribution. This realization led to the development of k0s, a distribution specifically designed to be lightweight and adaptable. The [**Lens IDE**](https://k8slens.dev/), being a Kubernetes IDE is a powerful Kubernetes-focused integrated development environment that simplifies cluster management, providing a centralized and intuitive interface for monitoring, debugging, and deploying applications streamlining Kubernetes workflows, making it a go-to tool for over 700,000 users monthly, found simplicity in deploying extensions on k0s, making it an ideal choice for those looking for a streamlined and efficient Kubernetes experience.

This adjustment aims to provide a more coherent and factually accurate representation of the development process behind k0s and its integration with the Lens IDE and other extensions.

K0s is simple to deploy as it is a single binary so it incorporates all Kubernetes components and dependencies, with all the components and attached dependencies that you can run the binary on various operating systems.

# Zero - Concept

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702810616338/6de43440-5180-4aaa-9cc3-41ea364d3be6.png align="center")

We know that while handling Kubernetes we often say it as K8s because of the number of digits in the word Kubernetes between K and s, but in k0s it didn't have any letters to be filled in between but due to the various features that make k0s unique from any other distro:

#### **<mark>Zero Friction</mark>**

k0s drastically reduces the complexity of installing and running a fully conformant Kubernetes distribution. Clusters can be bootstrapped and deployed within minutes. Less toil for developers during deployments allows them to focus on what matters most. The installation and management processes are designed to be user-friendly, minimizing hurdles and complexities. This approach reduces friction points, allowing users to deploy and maintain Kubernetes clusters with ease.

#### **<mark>Zero Deps (Dependencies)</mark>**

k0s is distributed as a single binary with no host OS dependencies besides the host OS kernel which signifies that k0s is designed to be self-contained and independent. It works with any Linux operating system without additional software packages or configuration. Security vulnerabilities or performance issues can be debugged and fixed directly in the k0s distribution. It strives to have minimal external dependencies, reducing the reliance on additional software or libraries. This minimalistic approach simplifies the installation and ensures that k0s can operate efficiently without introducing unnecessary dependencies.

#### **<mark>Zero CVEs</mark>**

The "zero CVE" aspect underscores k0s's commitment to security. By aiming for zero Common Vulnerabilities and Exposures (CVEs), k0s emphasizes a proactive approach to addressing security issues. k0s installs Mirantis-curated versions of current upstream Kubernetes binaries, with known CVEs minimized, and new CVEs removed as rapidly as possible. Version 1.27, at release, had zero known CVEs. Regular audits, prompt fixes, and a focus on secure coding practices contribute to a Kubernetes distribution that prioritizes the safety of users' deployments.

#### **<mark>Zero Cost</mark>**

k0s is completely free for personal or commercial use, and it always will be. The source code is available on [GitHub](https://github.com/k0sproject/k0s) under Apache 2.0 license and will be continuously updated with all the latest Kubernetes features, without delays. It’s an essential foundation for any Kubernetes project and easy to build upon.

# K0s Provisioning

We generally have three different types of k0s provisioning:

## Binary

Here if we need to work with a single node, we may start with the curl command and start the Kubernetes with:

```bash
curl -sSLf http://get.k0s.sh | sudo sh
sudo k0s config create > /etc/k0s/k0s.yaml
sudo k0s insteall controller --simple -c /etc/k0s/k0s.yaml
sudo k0s start
```

`curl` command fetches the k0s binary from the specified URL and installs it using the `sudo sh` command. It's important to note that using `sudo` grants the installation script the necessary permissions to set up k0s system-wide.

The `k0s install controller` command sets up the k0s control plane. The `--simple` flag indicates a simplified installation mode, and the `-c` option specifies the path to the configuration file (`/etc/k0s/k0s.yaml`). The controller includes components like the Kubernetes API server, controller manager, and scheduler.

Finally, the `k0s start` command launches the k0s components, bringing up the Kubernetes cluster. This step completes the setup process, and your k0s-powered Kubernetes environment should be operational.

## CLI

Here if we need to start with multilevel nodal clusters and start using k0s with the yaml dependencies started by k0sctl:

```bash
k0sctl init > k0sctl.yaml
cat k0sctl.yaml
k0sctl apply
```

To check out the yaml dependencies, the init command will create a complete yaml description of your deployment once we have tweaked all these different parameters. We just need to call Rest API to file and basically, it will deploy k0s across various nodes to have more complex and highly available deployments to get access to your k8s clusters and nodes taking about a few hours/ minutes depending on the complexity and scale of your clusters.

## Controllers

```bash
cat cluster.yaml
kubectl apply -f cluster.yaml
```

Here in this provisioning, we can also leverage more advanced controllers like cluster API, which is an example of cluster API definition that shows that we can deploy the cluster in terms of resources.

It also does not take a lot of CPU and memory resources by acting as an adapter to all kinds of cloud services. It is also a real asset for our environment where we have physical servers that do not hold a lot of CPU/ memory space or where systems hold a lot of CPU restrictions by, let's say only allowing x86 architecture and restricting any other architectural system like x64 or remaining 7 architectural hardware where we expect lesser memory utilization, thus making it a unique and useful cloud solution.

---

Based on Upstream Kubernetes, K0s has many other advanced features. For instance, support for Role-Based Access Control (RBAC), and Open ID is provided out of the box, GPUs, and Horizontal Pod Autoscaling (HPA) are also available. K0s can be installed on both Intel and Arm architectures and can run on any Linux host or Windows Server worker nodes.

Hope you get to know some great insights about what you came to hear about, and this article would have been able to add some value to your knowledge. Soon, I will be making some other detailed blogs about projects like k0s motron, terraform, k3s, Rancher, Grafana and a lot more.....

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702821394615/2af72712-5c73-4554-a789-0b99b74255af.jpeg align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)