---
title: "Kubernetes: The Rocket Fuel for Cloud-Native"
datePublished: Fri Apr 21 2023 12:56:13 GMT+0000 (Coordinated Universal Time)
cuid: clgqk22n5000j0al1ayyw5dwl
slug: kubernetes-the-rocket-fuel-for-cloud-native
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682081323141/416f0447-bef0-454f-9007-8f3892911120.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682081687349/494664ee-297d-418a-bb95-dc90188af431.jpeg
tags: kubernetes, cloud-computing, devops, 2articles1week, wemakedevs

---

Kubernetes is an open-source container orchestration system for automating software deployment, scaling, and management. Originally designed by Google, the project is now maintained by the Cloud Native Computing Foundation. The name Kubernetes originates from Greek, meaning 'helmsman' or 'pilot'.

It is the general definition that you will find on the internet telling out about its orchestrational ability but in reality, it's a far better tech with a lot more features oiling up the whole Cloud Native ☁️ domain.

## Difference between Cloud-Native & Cloud Computing

Before getting to know about the most important tool of cloud-native let's figure out what cloud native is and clear up the confusion between Cloud-Native and Cloud Computing.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682075240387/9af6bccc-311f-4ae8-bfa9-7b89e680230b.jpeg align="center")

Cloud Computing provides computer system resources, especially data storage and computing power, without direct active management by the user. It provides some on-demand system resources, and data storage such as RAM, memory and much more stuff. Leading providers in this field are Amazon Web Services (AWS), Microsoft Azure, Google Cloud Platform, IBM, Oracle, etc. Although these companies also provide some amazing cloud-native services &tools as well they are primarily cloud-computing companies only.

While one of the other newer players, Civo (developed in 2018) is a cloud computing company that focuses on providing a Kubernetes platform for developers, with a strong emphasis on cloud-native technologies and practices.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682075419382/57d46c7b-0e83-485d-bf11-ba3693b3f8f7.jpeg align="center")

Cloud-Native should satisfy and run on Modern day Business models which are-

* Zero-Downtime
    
* Easy Scaling
    
* Heal Containers
    
* & Should run on **KUBERNETES**
    

Earlier various forms of tech were used such as Configuration Management, Package Managers, etc-

* **Configuration Management**
    

It was a management tool that was used to manage data whenever we wish to change our data. It was also used to keep track of how much RAM should be dedicated to being used by Virtual Machines. It benefited in the better reliability of the system as if let's say 10GB of data is been dedicated to Virtual Machines and we used only 2GB of it then the remaining 8GB of data is wasted which could have been used by the main computer but since the given data is large and neither it is been used so it will surely interrupt with the main functioning of our computer.

* **Package Management**
    

At various times we often find that a particular application runs on a particular version of the software and another feature of the same application uses another version of the same software which will eventually become a lot more tedious to work with thus Package Managers came into the picture where with docker as well we can easily install, use and deploy any version of the software with any problem.

# Managing Containers

## Monolithic Applications

In a Monolithic application, deploy different applications such as frontend, backend, chat message, database and networking or various other applications as well as a single application as a bundle. The major problem faced with it was that whenever we want to introduce some new features or some changes then the whole system will be stopped thus stopping other applications as well even when they don't have anything to get changed which also retards scaling up the server.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682075439515/4227867d-d202-4535-82da-c30d535fa669.jpeg align="center")

## Microservices

To tackle this problem of monolithic applications, Microservices were introduced which deployed each application as an individual application or container as a result of which the downtime could easily be maintained, fault isolation, and bugs could be found much more easily and the application could run seamlessly without dealing with much of problem. But the major problem which is faced here in this process is:

* How to Manage them all easily?
    
* How to communicate?
    

as they all are separated as individual applications, So the major tool used to deal with these problems is **Service Mesh.**

Now lets, say we wish to make any changes to our application without any downtime or let's say that load on our server increased then we may wish to distribute the load on our server in just one click which can be done with the help of Orchestrators. They help us in deploying and managing our containers dynamically with

* Zero-Downtime
    
* Easy Scaling
    
* Healing Containers
    

which are also the features of Kubernetes and requirements of Cloud-Native applications. Kubernetes also provides a lot more features than just orchestration.

Kubernetes can be run on our system on the cloud service providers and can migrate from one provider to another provider.

It can Replicate services, Scale those or put them on dedicated servers with Zero- Downtime, Self-Healing of clusters, Vlomes can be used, external storage, load balancing, access log, service discovering & can also store secret information like passwords.

# How is Kubernetes formed?

So earlier in 2006, **Amazon Web Services (AWS)** came into the cloud computing which dominated the whole market along with it a lot more cloud computing software like **OpenStack** also came to compete with it but they can't make it to the end and got shut down soon.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682075519285/1e1a204a-4251-4053-a684-90d9619b52bc.jpeg align="center")

While these all events were taking place we get to know that Google was running their cloud-native privately already and using Billions of containers at that time within the project names of **Omega & Borg**. Later Google renamed Borg as **Kubernetes** and donated it to **Cloud Native Computing Foundation(CNCF)** and made it **Open Source**. Also, Kubernetes is also called **K8s** as it contains 8 words between k and s in the word Kubernetes.

The major difference between Docker and Kubernetes was that Docker was a container tool and Kubernetes acts as an orchestrator. We were able to run everything in Docker but it was sort of deprecated as it uses **CRI**(Container runtime interface). Kubernetes can use various CRIs like container d but it isn't allowing us to use Docker as it doesn't comply the standards or OCI(Open Container Initiative).

# Kubernetes Clusters

**Clusters ------------&gt; Control Plane + Worker Nodes**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682076070135/6890efa0-fa60-4a0c-98a5-716672b1b0fd.png align="center")

In short Worker nodes, may be taken as servers and the Control plane is where we can manage these containers, we will soon be discussing in brief about them all in the next section below.

KubeCTL is like the Kubernetes CLI(command line interface like docker, git, etc) which communicates with the control plane which will see which worker node is empty at the moment so that u can use KubeCTL in two ways-

* **Declarative**\- writing manifest files like writing codes in YAML for example and then giving them to run.
    
* **Imperative**\- Telling out clusters for some command to assign some function to them.
    

## Pods

Amongst various tools, pods are used as the Scheduler unit of Kubernetes.

Similar to the container, a pod is a scheduling unit and inside the pod is a container.

* Require your web app & then create Microservices.
    
* Containerize your web app
    
* Put containers in pods
    
* Deploy the pods to controllers.
    

---

## Controllers

In Kubernetes, Controllers are control loops that are used to watch the state of your cluster, then make or request changes where needed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682076096131/f7e68232-3bfb-4183-859e-f73a8d785f1b.png align="center")

Each controller tries to move the current cluster closer to the desired state. For example, if we command Kubernetes to always run 5 pods then controllers are the place where this command goes to Kubernetes and has been taken care of it.

Deployer is one of the built-in controllers in Kubernetes. In Kubernetes, containers work on top of Virtual Machines, like there are nodes that can be Virtual Machines and we can run Kubernetes on them.

---

# Control Plane

In the starting, it was called master node but then later renamed as control plane as it was not the proper naming convention.

Anything like managing or destroying pods and clusters in Kubernetes is decided to be controlled and managed by Control Pods which might also run on multiple computers in the production environment.

## The Architecture of Control Plane

KubeCTL will be like an API server managing the number of pods to be running on the system. It also manages the deployment out of the file containing that deployment file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682076119426/60417396-5391-4d14-9abc-fce464598494.png align="center")

### **API Server**

It will be responsible for all communications. It exposes a restful API where you can give it in a post API like in getPost. In HTTP we can give it some YAML file(YAML files act as Kubernetes manifest file) containing some pod definition or information on which container or image should follow or act according to it.

### etcd

Etcd is an open-source distributed key-value store that is used to store and manage the information that distributed systems need for their operations. It stores the configuration data, state data, and metadata in Kubernetes.

The name “etcd” comes from a naming convention within the Linux directory structure: In UNIX, all system configuration files for a single system are contained in a folder called “/etc;” “d” stands for “distributed.”

It is the one solving the second problem faced in the case of microservices which was to maintain proper communication between its components k8s needs a data source that can help with the information about all the components, their required configuration, state data, etc. That data store must provide a consistent, single source of truth at any given point in time. In Kubernetes, that job is done by etcd. etcd is the data store used to create and maintain the version of the truth.

### **Controller Management**

It takes care of controllers & it has 4 major functionalities

* **Desired State**, if the API is requesting for 5 pods to be running then the constant running of these many numbers of pods, is to be managed by it.
    
* **The current State** looks out for the problem that might be seen while working with the Desired state controller management.
    
* **Difference** follows out and tells out the major difference
    
* **Make changes**\- Like if someone is asking for some changes to make, so here it manages them all and make changes to them.
    

### Schedulers

It is used for scheduling in Kubernetes. If I am asked to make some pods so Scheduler is the one who will schedule it on the worker node by looking if the specified worker node is empty, does it contain any container, networking requirement, or images for running the container, downloaded or hat is already running on node & if it isn't free then it will all be pending still.

---

Also if along with the Control Managers if you are using some cloud providers then they will be running/ using their control managers for balancing the load on servers.

API server listens to HTTP via Port 443.

---

# Kubernetes Architecture

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682076146042/42b05eaa-6958-4957-aeeb-57376032f819.jpeg align="center")

**Kubelet** is on every worker node, any worker node created will have kubelet attached to it.

So let's say KubeCTL CLI asks for the making of 5 pods then the request will be made to the API & Kubelet is attached to every container and the API server, so if any request is made then Kubelet's function is to look into it and make it happen.

In case, it can't do then it will ask the control plane that it can't do it then the scheduler & etc d will come into play.

In Kubernetes, earlier Docker was supported but then later it wasn't supported as it doesn't support OCI (Open Container Initiative) in place of Docker came Container-d which supported CRI which was a container runtime interface & it is also responsible for building up, managing, changing, deleting and a lot more stuff as well which wasn't supported by Docker hence Docker was replaced by Container-d.

If our worker-node & clusters want to communicate with an outside network Kube-proxy is used, which is generally for networking requirements. Kube-Proxy also makes sure that every worker node gets its Unique IP Address & **the remaining parts of the architecture have been described in brief earlier** in the control plane architecture and in various other sections as well.

So to communicate with each other (pods) have their own K8s DNS or Core DNS which is done with the help of the IP address of each pod.

Pods are the smallest Scheduling unit in Kubernetes. You can't schedule a container without pods & then you can schedule pods inside deployments, scale or update pods.

# Getting Started with Kubernetes by setting it up in your system!

So to start working with Kubernetes we will have to download Kubectl first.

```bash
Kubectl version --output=yaml
```

To start running kubectl in your terminal command line.

```bash
minikube start
```

It is written to start using minikube which is recommended to use for beginners to just start with it if we don't have any cloud provider subscribed yet or any other stuff. It can perform all advanced level functions as well and can be used by advanced level practice as well.

minikube has one cluster which will create and add resources to it & that one cluster will act both as a control plane and a working node. It will create a new Virtual Machine based on minikube image & will contain a few binaries, container runtime, etc everything required to run Kubernetes.

```bash
minikube status
```

To watch out for the status of our Kubernetes clusters, images, etc.

```bash
kubectl get pods
```

To get a list of all the pods running at the moment on the system.

```bash
kubectl get nodes
```

This will list all the nodes running at the moment in the system.

```bash
minikube docker-env
```

Will give a list of all the variables required for your client on your system to communicate with the local server.

```bash
docker container ls
```

Will list all the containers in Kubernetes.

Everything in these Virtual Machines is running inside the container so you can have a view of containers running inside minikube as well as:--

```bash
minikube ssh
```

to get inside the minikube so that you can get information about various things inside this minikube about containers or anything else either by writing

```bash
docker container ls
```

or

```bash
docker ps
```

to view the containers running inside this minikube

```bash
kubectl get pods
```

to view all the pods running inside Kubectl

```bash
kubectl get all
```

It will give you all the info like the pods running at the moment, services running, deployment & replicate running.

```bash
kubectl delete pod <name_of_pod>
```

This will allow you to delete the pod entered name.

# Pod Manifest file

Now to create Pod a general Yaml file like the one below can be generated including various specifications:

```bash
apiVersion: v1
kind: Pod
metadata:
    name: nginx
spec:
    container:
        -name: nginx
        image: nginx:1.14.2
        ports:
           -containerPort:80
```

**apiVersion**:- Defines the version of Kubernetes API you are using to create this object.

* ***v1***: means Kubernetes object is part of the first stable release of Kubernetes API. So consist of a core object such as Pods, Replication Controller & services.
    
* ***app/v1***: include functionalities related to running apps in Kubernetes.
    
* ***batch/v1***: consist of objects related to bash process & jobs like tasks.
    

**kind**:- Means what type of resources we are trying to create.

**metadata**:- Data that help uniquely identify the object, including a name string, UID & optional namespace which can attach name & label, etc.

**spec**:- Contain format of the object spec from every Kubernetes object like for name, image, etc.

these are used to create pods by writing code out of them properly like creating a YAML file in a dedicated folder as written above in the terminal.

# Some Important Tools

There are many important tools that are used every day to make things go in a smooth and frictionless manner. Soon in the next series of Blogs, we will be going, in brief, to know their functionality at the moment let's just get a quick glance which are some of the really amazing and important tech.

## **Lens IDE**

**LensIDE is the largest and most advanced Kubernetes platform in the world with over 700k monthly users doing what we can surely say is MAGIC.** It will show up all clusters, pods, containers, deployments and all of your running, CPU and memory storage in it and a lot more amazing features.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682078759323/812909da-03be-4395-b550-24e648f25601.png align="center")

It also has features to connect to our online clusters if we are working with cloud providers like Civo, AWS, Google Cloud, Azure, etc. It also makes up the dashboard for all the clusters, pods, and Deployments and also helps in writing up & managing big-big YAML files. *We will surely be bringing you a lot more insights to this tool in brief in the next dedicated blog individually to clear up all its functionalities.*

## Kubeshop

When YAML files become very very big then it becomes very difficult to manage them and here we use Kubeshop there which comes with a tool called:--

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682079388316/f8e27c54-9e13-4d62-a190-a5e2a37205fb.png align="center")

### **Monokle**

**Monokle is a set of tools for creating and maintaining high-quality Kubernetes configurations throughout the entire application lifecycle.** It helps in managing & debugging our Kubernetes manifest files. It helps in managing big files & navigating those into a very nice presentable form.

## Datree

Sometimes while we are creating Kubernetes manifest files, we end up with making thousands or more of such manifest files which might result in making some violate some rules which could be checked before it reaches production.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682080362868/5719eb03-67c7-4eec-bd6d-ef3361949789.png align="center")

When we push our git repository & when it is running CI/ CD checks at that time only before reaching production, Datree tells out the misconfigurations based on some in-built rules which can also be made by us and added to the list of those rules to check. It is an amazing tool being used by everyone to check their manifest files to save time in finding errors and improving their code.

## Teleport

Teleport prevents phishing by relying on biometrics and machine identity, stops attacker pivots with the Zero Trust architecture, is compatible with everything you have, comes as a cloud service or a self-hosted option and doesn't get in the way of an engineer's productivity.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682080609636/91b7aa7e-c954-46f5-ad17-596db4c4410e.png align="center")

Teleport provides an automated and holistic view of all privileged infrastructure resources within your organization. This eliminates access silos, protects from impersonation attacks and provides a single place to manage policy.

I will soon be releasing some dedicated blog briefings about the functionalities of all these AMAZING tools soon.😄🔥

Thanks for reading! I hope you found this introduction to Go helpful and informative. If you have any questions or comments, feel free to reach out to me on Twitter:

My Twitter Profile: [Aryan\_2407](https://twitter.com/Aryan_2407)

I'm always happy to connect with fellow tech enthusiasts and answer any questions you may have. Don't forget to follow me for more updates on tech, programming, and more.😄🔥