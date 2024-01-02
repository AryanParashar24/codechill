---
title: "Knative enhancing Eventing & Serving in CloudNative"
seoTitle: "Knative enhancing Eventing & Serving in CloudNative"
seoDescription: "Knative is one of the fastest growing Open Source project of CNCF, enterprise solution for building severless & event driven application"
datePublished: Tue Jan 02 2024 20:50:41 GMT+0000 (Coordinated Universal Time)
cuid: clqwtqbg7000308lhdu7n0pdc
slug: knative-enhancing-eventing-serving-in-cloudnative
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704209228905/f8b86148-7bfd-4dad-ab84-965e9382d8b9.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1704228548685/dc18c6c2-c64e-4ddd-8ccb-557a81e2b115.jpeg
tags: software-development, software-architecture, kubernetes, cloud-computing, devops, software-engineering

---

Knative is one of the fastest growing Open Source project registered in the CNCF Incubating project list, which is an enterprise solution for building severless and event driven applications. It was developed and announced by developers at IBM, Google and a number of other industry leaders.

Knative is a platform installed on top of Kubernetes and essentially brings capabilities of server lists and running service workloads to Kubernetes. In addition it provides a number of utilities that make working with with Cloud Native applications on Kubernetes feel truly native.

Knative can also help in scaling pods to thousands or to zero, if nobody is using the application which can help in **Efficient Resource Utilization,** thus we can get URL to our code without writing any deployment files, ingress, rules or without taking care of any certifications, etc.

It can also manage and responds to Cloud Native events, so there could be publishers, subscriber in which we can have advantage of eventing.

# Components of Knative

There are three major types of components of Knative:

1. Build
    
2. Serve
    
3. Event
    

which are the primitive, as these are the building blocks of Knative and allow it to run serverless workloads within Kubernetes, it also provide endpoints and tools to make working with Knative felt more natural and easy to work.

Although, the bring component was a part of Knatiev but now, it has been moved to tecton pipelines. Although we can use certain Build Tools like KaniKo, Buildia, Docker, but we will still be discussing Build component.

### **Build**

Developer need to do certain tasks to push these applciation s to Kubernetes as:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704212757180/f5119dda-52ca-4f15-be8a-f745813ada88.png align="center")

1. Produce code for theori applciations which might be hosted on GitHub so that every developer get access to it.
    
2. Now, we need to pack up our code to the containers, so that Docker or Kubernetes can understand and get access to it with docker build as the simplest process or any other approach depending on how complex your build is, to end up with final image.
    
3. Now we need to push the image to a repository like Docker Hub or any other private image registery so that Kubernetes can get access and deploy it.
    
4. Create some manifest files and depending on how complex your deploy is, we might have multiple YAML files for deployment.
    
    For a developer who is iteratively working on top of Kubernetes, it would be a really tedious task to perform. Thus, with Knative all of these features can be brought on your Kubernetes cluster, so everything from source code, management of complex or custom builds or even if you want there are a number of Templates out there.
    

With Knative build, you can do all of these within your cluster which eases out the work for developers in the iterative process and all of these processes can be simplified into a single manifest deploy to become more faster and more agile to develop applications.

Serve and Events components will be discussed while explaining the modern components of Knative.

### **Infrastructure Layers**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704216309835/93c82306-4d62-4f5e-b866-04cddc97ebae.jpeg align="center")

Here our Infrastructure layer would be present on top of which we would be having Kuebrnetes layer, on top of which we will be having our Knative layer for autoscaling, scaling to zero, intelligent routing, traffic splitting, different tags for different routes, Revisions and out of the box certificates management.

So, we will be having our code and functions which have just containerized in the process. To build our image we can use tools like KaniKo, Buildia and Docker.

**<mark>Modern Components of Knative</mark>**

We have 2 parts at Knative:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704217063857/84a276ba-bfb9-4f0b-8659-c5f36c168568.png align="center")

Serving will help in Auto Scaling, Revision and Traffic Splitting, while the Eventing will proceed with Cloud Events or Sources forwarding events to brokers or Triggers which will route to a specific service or the sync and that Trigger can also send to a Knative Serving and Eventing can be a powerful combination btu they can be fully runned independently.

## Serving Independently

When we will be installing serving in our Knative environment, we would be applying :

* CROs
    
* Serving core
    
* Networking Layer like Kourier, Istio, Contour
    
* Patch Native surveying to use Kourier
    

Then we can use the auto DNS with certificates like TLS or HTTP01 or we may use search manager as well so there are other ways we can get auto TLS like:

Created Container -&gt; Deploy source on specifications in services -&gt; Then after everything got created automatically with HTTPs endpoints.

# Serving

Whenever we will be creating a service, it hits a particular URL, let's say we deployed a service and you hit it for the first time then, the request will go to the Activator first, now Activator will ask Auto Scaler to Scale up one pod to serve that request.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704220247262/6c275a3b-d838-4bea-9709-a5bbace32287.jpeg align="center")

Default Auto Scaler here is KPA, although you can also use other services for auto scaling like HPA, which can do like a CPU based utilization, matrix calculations which Knative KPA can't do. We can also define the scale up or scale down rate, the maximum scale rate, so that we can have 1 pod running or if don't then scale it down to zero.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704220899934/bd5780cb-4e72-467a-87d8-34dcd85b78a4.jpeg align="center")

If the first flow process is over whenever we hit the service what happens is, there is a Queue container inside the pod then we have user container which will hold our application and then, if we have Istio or any other container then it will be present below the suer in the pod, like Envoy.

Queue container will be taking care of metrices and we will be keeping eye on concurrency. For example, i concurrency is set to 100 then, once it goes beyond the limit then it will request HPA or KPA auto-scaler to spun up a new pod.

Then for a service, you can create different revisions and you can also do traffic splitting of your chosen ratio. It help sin intelligent routing and traffic management and automatic scaling. Let's say in the process we start a service, kind of a Route and a config.

Everytime a push is done, it will eventually be stored and keep that revision stored, as let's say in the example we have got a Revision 1 and Revision 2 where, Revision 2 will be the update of our application been pushed later, so config is actually going to manage both of them.

Using Istio traffic management or any other tarffic management services will let us manage to route 10% of traffic to Revision 2 and rest 90% to the Revision 1 to start planning to be staged rollout or can perform AB Testing.

Thus, Knative serve provides an intelligent routing as well as scaling and solve out a lot of problems for people performing CI/CD doing micro services deployment to Kubernetes.

There are some other amazing features being provided by the Knative in Serving as:  

**<mark>Easy Roll Backs</mark>:** To roll back to previous revision.

```bash
kn service update <service_name> --traffic <revision>=100
```

**<mark>Tag</mark>:** tag revision to directly list a particular revision. Example: `first.<default_nameOfServcie>`, so we can get there tags to revision as well and also default revision.

**<mark>Rollout</mark>**: So we can do the gradual rollout to the new revision as well, but have a CD solution in place for production like setups where we can check the SLOs and other stuff such as **Keptn.**

# Eventing

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704228121129/fc5d0ecc-39a7-40f6-8631-37335816ebd2.png align="center")

Eventing is basically for event driven architectures so it's called Knitting, majorly for which Knative was built at first place and got K in the starting of it's name. It was very carefully taken how to decouple stuff so there's a lot of decomposing like independent producer consumer everything based in Cloud Event which is another CNCF project for standard event formatting so different components that form up Knative eventing in the source.

Source gets the events inside the cluster like it ingress all the events inside the cluster and are the **Primary Event Producers**. So inside the Cloud, it will be producing and these events will be sent to the Broker.

Now, there are 2 types of Routing Tech. both are used:

* Broker Trigger tech.
    
* Channel Subscription
    

### Broker - Trigger Tech

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704225663163/300ec9d9-0c3b-4019-92da-8545ddbb32e5.jpeg align="center")

Routing takes place to the desired destination in the form of Function and Services. Uniformly distributes the traffic to it's consumers and consuming can directly register for a specific event.

**For Filtering out Triggers, we use Broker-Trigger, in case we want to filter out the event being forwarded to the sink.**

### Channel Subscription

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704226185962/adf4e12c-814d-4397-9aa6-06bee97d8f8e.jpeg align="center")

Channel Subscription are topology based routing which transform the event and then route to the process.

Sink are use for taking events to a destination, can be services, channels, broker. So sink can be directly calling the services, directly going to the channel or the broker.

## Use Cases

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704226864110/0f3796c0-10ff-43cc-86ce-7cd7fce0c6f7.jpeg align="center")

Here in this case, GitHub will be the place for hosting the project repository where we will be having the source and we want to get the events to our sink, which will later be shown at our Email.

Now, here we will be having a channel which can be inmemory, Kafka or any other service as well, associated to our source which will be having 2 services as in our case to be subscribed to the channel so that events reach to the sink and then to our Email.

Now, the same event will be selected from the channel to both the service and then will pass on these events to the sink to be show in our Email.

Now, in case we want our Events to be filtered and only filtered mails will be forwarded to the service 2 from the service 1, for which the Broker-Trigger technique will be used and the event will be passed on to Broker instead of Channel and only certain filtered events will be forwarded from the service 2 to the sink and then finally to our Email.

Hope, you got to know what you came here for and got some information added to your knowledge boundary. Soon, I will be sharing a lot more blogs detailed related to the CNCF Projects and Tools, impacting the world of CloudNative and whole tech domain, drop the comments if you want to request any detailed blog on any of the project you are excited about🚀🔥 So that I can clear any of your doubts in case you are feeling just like the domain below😄

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704228457660/a5cb6a77-1add-4ed4-8803-3d5318990008.jpeg align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)