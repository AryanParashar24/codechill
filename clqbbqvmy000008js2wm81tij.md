---
title: "K0s Motron - The Kubernetes☸️ Control-Plane Manager"
seoTitle: "K0s Motron - The Kubernetes☸️ Control-Plane Manager"
seoDescription: "In this blog, we will be learning about the K0s Motron: Kubernetes an operator-based multi-cluster manager that can deliver lots of Kubernetes clusters, dyn"
datePublished: Mon Dec 18 2023 19:44:04 GMT+0000 (Coordinated Universal Time)
cuid: clqbbqvmy000008js2wm81tij
slug: k0s-motron-the-kubernetes-control-plane-manager
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702928375916/b21fee8d-4054-4c3e-be65-2436072ccc3e.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1702928506551/8c08f5df-68f2-4c54-adad-04654b36230d.jpeg
tags: cloud, software-development, software-architecture, kubernetes, cloud-computing, devops, hashnode

---

In this blog, we will be learning about the K0s Motron: Kubernetes an operator-based multi-cluster manager that can deliver lots of Kubernetes clusters, dynamically, with minimum operations headaches in a few minutes!!

k0s Kubernetes is a CNCF-validated, easily customized, single-binary, almost-no-dependencies Kubernetes distribution that installs with one command pretty much anywhere (i.e., Intel or ARM, down to 512MB RAM, any popular Linux, in containers, etc.). The k0s project prides itself on keeping up with [kubernetes.io](https://github.com/k0sproject/k0sctl): security patches in under 72 hours, minor releases validated and provided to users in days. k0s deploys with one command anywhere, and brings along its own CLI and kubectl – with additional open-source deployment and operations tools available for download from Mirantis, e.g., [k0sctl](https://github.com/k0sproject/k0sctl), [Lens Desktop](https://k8slens.dev/)).

Once we are done with the setting up of our distribution with k0s which will run on top of your infrastructure, we need to find a component that will manage the life cycle of different Kubernetes as a Service offering, so you need to have a capabilities to manage all difference Kubernetes clusters and do it at different scales.

# Features & Usability

K0s is an open-source project, developed by Mirantis which can manage the life cycle of different Kubernetes clusters. It allows you to transition from a child cluster model. The default way of doing it is that in every Kubernetes cluster, we have a dedicated control plane and worker nodes.

[K0smotron](https://k0smotron.io/) is an open-source operator (runs on any CNCF-validated Kubernetes) that lets you host, scale, and lifecycle-manage containerized k0s control planes on a Kubernetes cluster, using Kubernetes-native methods – and then configure and attach workers to these virtual control planes from anywhere. K0smotron is being built to solve big challenges now being faced by organizations that want to leverage Kubernetes with agility and cost-effectively – with minimal need for platform engineering, special skills, and operations person-power.

**<mark>It provides various interesting insights, features and usability as:</mark>**

1. **K0smotron Unleashes Unparalleled Scalability and Flexibility:**
    

K0smotron offers a groundbreaking solution by enabling the creation and management of clusters within an existing Kubernetes cluster. This innovative approach provides unparalleled scalability and flexibility, especially in scenarios where multiple clusters need to coexist. The ability to maintain a homogenous setup for all control planes significantly eases the maintenance burden, ensuring consistency and efficiency across your Kubernetes environment.

1. **True Separation of Control and Worker Planes:**
    

One of the standout features of k0smotron is the true separation of control and worker planes. Similar to leading cloud providers, the control plane, residing in an existing cluster, operates without direct networking connections to the worker plane. This robust architecture enhances security and aligns with best practices, offering a level of isolation that ensures the reliability and integrity of your Kubernetes clusters.

1. **Bring Your Workers for Ultimate Flexibility:**
    

K0smotron introduces the revolutionary concept of bringing your own worker nodes from ANY infrastructure to your cluster's control plane. This flexibility breaks down infrastructure silos, allowing seamless integration of worker nodes regardless of their origin. The result is a versatile and adaptable Kubernetes environment that can harness resources from diverse infrastructures.

1. **CI/CD Agility with On-Demand Clusters:**
    

For CI/CD workflows, k0smotron emerges as a game-changer. The ability to create and delete control planes on-demand simplifies integration and end-to-end testing. No longer constrained by long-lived snowflake clusters, CI processes become dynamic and agile. Creating a control plane becomes as easy as defining a custom resource, bringing a new level of efficiency to CI/CD pipelines.

1. **Edge Computing Made Accessible:**
    

Deploying Kubernetes on the network edge can be challenging due to resource constraints. K0smotron addresses this challenge by allowing the control plane to run on an existing cluster, even on a separate dedicated infrastructure. This not only removes hurdles but also empowers teams to focus on the true edge computing challenges, making edge deployment accessible and efficient.

1. **Multi-Cloud Mastery:**
    

In the era of multi-cloud environments, k0smotron stands out by enabling the management of control planes (Mothership) in one cloud provider while deploying workloads across various others. This strategic approach streamlines multi-cloud operations, offering a cohesive and efficient strategy for organizations embracing the advantages of multiple cloud providers.

## Controllers & CLusters Mgmt.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702915107732/8a0b25a9-bc00-4928-b77e-a358335b0416.png align="center")

If we have free controllers to deploy applications on free nodes that can stand up to 1, 2, 3 or even more and similarities in Workload Clusters, which will be replicating the controllers and then taking as many worker nodes required to store the application in the child clusters of the same node.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702919143732/f9825199-65e9-4596-b906-7c34028c9d75.png align="center")

Now, the K0s Motron works in a bit different way in which we don't need to create these replicate these controllers or need to deploy dedicated control plane nodes for each child cluster.

Here we will be hosting only three free controller nodes and within these free controllers, we will host all the control plane services for all track listers. Then at the end, we containerize the control plane of tri clusters and host the pod in the main control plane of <mark>Management Clusters</mark>, where we can see a management cluster where we run our K0s motron, with only three clusters and for all our track cluster will have dedicated workers whether it is virtual machines or physical.

The main advantage of using K0s Motron will be reflected by 50% fewer clusters and control plane nodes than in general cases, thus lowering half of your licensing cost. So while using public clouds, you are not paying for ec2 instances, hence saving a lot on your operation because we aren't only dispatching nodes in the management cluster but also workload clusters, thus dividing them into 2: Operational and Maintenance for these clusters, as compared to the K0s motron because we have lesser nodes and have allocated all the services within only these free control plane nodes.

Thus, imagining them at a scale of hundreds would save a lot of amount due to their higher efficiency and cost-effectiveness. Thus a reduction in operational complexity is quite important, by K0s Motron as a Kubernetes as a Service which enables us to reduce massively your underlying infrastructure footprint.

# Internal Architecture

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702919149770/9e5d45e8-31ab-4f65-86a3-024bfb275085.png align="center")

Here we have 2 components, one is the management cluster which is your Kubernetes cluster which we built using K0s in this case, so it's the primary Kubernetes instance where our Kubernetes remaining and we will install K0s motron, which is the operator which acts as a controller and also acts as its own CRD (Custom Resources Definition). CRD allows you to define custom resources and their properties in a Kubernetes cluster. These custom resources can be managed and operated like any other built-in Kubernetes resources. They enable you to extend the functionality of Kubernetes by introducing your resource type.

Now, we can start to build different child clusters where we define the properties of our clusters in a yaml file and ask the controller to consume YAML file and ask the controller to consume the YAML file to deploy your Tri-Cluster when K0s motron will deploy our child cluster, the control plan will be hosted as a bus within the management cluster.

In the intricate architecture of K0s Motron, a pivotal component in the K0s project, a two-fold structure unfolds. At its core lies the Management Cluster, a keystone Kubernetes instance crafted with K0s, orchestrating the entire setup. Complementing this, the K0s Motron steps onto the stage as both an operator and a controller, donning the role of a custodian for child clusters. As an adaptable nature of K0s Motron within the architecture with its own Custom Resource Definitions (CRDs), K0s Motron consumes YAML configurations to breathe life into these child clusters. When summoned, a child cluster's control plane takes residence within the Management Cluster, offering a centralized nexus for orchestration.

This architectural symphony offers scalability, isolating child clusters, optimizing resource usage, and enhancing configurational consistency. Each child cluster, an independent entity, is defined through YAML configurations, affording flexibility and customization. In this intricate dance of components, K0s Motron not only defines the orchestration but becomes an enabler for users to architect a scalable, efficient, and customized Kubernetes ecosystem. As you delve into this realm, consider contributing to the K0s project, exploring CNCF and Linux Foundation initiatives, and showcasing your journey in a portfolio—each step propelling you towards coveted opportunities like Google Summer of Code and rewarding remote positions. Engage, contribute, and let this architectural ballet be the canvas for your tech odyssey.

# Difference between K0sMotron & other control plane solutions

We have various options in terms of hosting control planes for containerizing control planes and holding virtual clusters in K0s motron, which helps in managing multiple isolated and independent Kubernetes clusters, within the same physical or cloud infrastructure:

1. <mark>Infrastructure:</mark> Each Virtual Cluster managed by K0s Motron operated as an isolated instance of a Kubernetes cluster, which ensures resources, configuration and workloads within one Virtual Cluster don't get to interfere with those in other Virtual Clusters.
    
2. <mark>Flexibility &amp; Versatility:</mark> K0s Morton provides flexibility with Kubernetes solutions and environments. It allows you to run multiple Virtual Clusters, each serving different purposes to teams with a single infrastructure.
    
3. <mark>Version Management:</mark> Virtual Clusters can support different versions up and running all together for workloads.
    
4. <mark>Resources Efficiency:</mark> Support efficient resource utilization, instead of deploying separate physical or Virtual Machines for each K0s Motron enables to create and management of multiple Virtual Clusters in infrastructure.
    
5. <mark>Ease of Management:</mark> K0s Motron simplifies management of these Virtual Clusters through its capabilities, can define and configure Virtual Clusters using Yaml files, specifying parameters like external IP address, target version and many more.
    

The interesting part about the K0s Motron is not only related to one single solution, but it can run on any Kubernetes cluster as long as it is a standard solution, it can run on any Kubernetes solution, so we don't need to have K0s motron and your management cluster can be Open Shift by RedHat or Wrencher.

In the case of service control manager K0s Motron has only essential services within the control plane so very few services like etcd database and CubeAPI (which refers to a Kubernetes API server and is a core component of Kubernetes cluster) were only available to the footprints of services, and the main reason behind it was to scale out the number of control planes that we can manage within the management cluster, thus all the required services like Q proxy or core DNS were all hosted on worker node.

# Installation and setting up of K0sMotron

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702927606850/956cbc38-9511-4820-9d42-dacb9ab783db.gif align="center")

After we are done with downloading [Lens IDE](https://k8slens.dev/desktop.html) and k0sctl on our command/ control machine visit the [k0sctl Releases page](https://github.com/k0sproject/k0sctl/releases) and download the latest release of k0sctl, make it executable if necessary, and add it to your $PATH.

#### **Deploy your k0s “mothership”**

Create a k0sctl.yaml file for k0sctl on your laptop, as follows:

```bash
apiVersion: k0sctl.k0sproject.io/v1beta1
kind: cluster
spec:
  hosts:
  - role: controller+worker
    installFlags:
      - --no-taints
    ssh:
      address: 
      keyPath: 
      user: ubuntu
  k0s:
    version: v1.28.2+k0s.0
```

This describes a minimal single-node cluster in k0s’ default configuration. The --no-taints flag enables workloads to be scheduled on the same node as the control plane (not a best-practice, but okay for a demo).

Apply the above config with k0sctl to build your one-node mothership on your first AWS instance.

```bash
$ k0sctl apply --config path/to/k0sctl.yaml
```

Deployment is usually complete in under three minutes. Please check the docs for more details on [k0sctl usage](https://github.com/k0sproject/k0sctl#usage).

Once the cluster is deployed, you can use k0sctl to retrieve a kubeconfig for the mothership cluster, and write it to a local k0s.config file:

```bash
$ k0sctl kubeconfig --config path/to/k0sctl.yaml > k0s.config
```

You can then start Lens Desktop, click + to add a new cluster, and copy/paste the kubeconfig into the editable pane. Click Save and your cluster will be added to Lens. Double-click on the cluster name to connect and view its internals. More information on using Lens Desktop can be found [here](https://docs.k8slens.dev/getting-started/install-lens/).

![Figure 1. Single-node “Mothership” cluster seen in Lens.](https://a.storyblok.com/f/153547/1847x551/fefeacea44/mothership.png/m/635x0/filters:quality(95) align="left")

Note that Lens normally does not count control plane nodes as ‘Nodes,’ because they don’t run a kubelet. In this case, we’ve created a single node cluster, so what you’re seeing identified as a Node here is its worker part.

#### **<mark>Install k0smotron</mark>**

Once you’ve connected to your Mothership cluster with Lens Desktop, you can use the Lens built-in terminal to give kubectl commands to the cluster.

To install the k0smotron operator, click Terminal at the bottom left of the Lens UI, and enter the following command:

```bash
$ kubectl apply -f https://docs.k0smotron.io/stable/install.yaml
```

For more amazing insights about the project reach out to the official documentation of this project at [https://www.mirantis.com/blog/getting-started-with-k0smotron/](https://www.mirantis.com/blog/getting-started-with-k0smotron/)

To engage & collaborate on team reach out to their Github: [https://github.com/k0sproject/k0smotron](https://github.com/k0sproject/k0smotron)

Hope you get to know some great insights about what you came to hear about, and this article would have been able to add some value to your knowledge. Soon, I will be making some other detailed blogs about projects like Terraform, k3s, Rancher, Grafana and a lot more.....

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702927959676/f6a7db74-557b-4855-bc94-fe8e01473e0b.jpeg align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)