---
title: "Effortless Kafka Streamlining on Kubernetes using Strimzi"
seoTitle: "Effortless Kafka Streamlining on Kubernetes using Strimzi"
seoDescription: "Discover how Strimzi revolutionizes Kafka deployments on Kubernetes, offering automated, scalable, and easy-to-manage solutions in your Cloud Native-env."
datePublished: Wed Jun 26 2024 14:33:49 GMT+0000 (Coordinated Universal Time)
cuid: clxvxrl6f000308mga6gnffhb
slug: effortless-kafka-streamlining-on-kubernetes-using-strimzi
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719409286606/08d5c3e9-c25e-498c-96f7-f8dcf0d83caf.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1719409489760/590c8558-fb00-49f1-a3a0-e19a597cce5e.jpeg
tags: cloud, software-development, kubernetes, cloud-computing, devops

---

## Kafka

Kafka is a distributed messaging system based on public-subscribe model. Apache Kafka is an open-source, distributed event streaming platform. It excels at handling high-volume data streams in real-time, enabling efficient data pipelines, stream processing, and event sourcing. Originally conceived for message alerting, it has evolved into a powerful platform for publishing, subscribing to, and processing continuous flows of data, making it a cornerstone of modern cloud-native architectures due to its scalability, fault tolerance, and high availability.

### How it started and How it's going now?

Apache Kafka began as a high-throughput, distributed messaging system developed at LinkedIn to handle massive data streams. It was designed to efficiently publish, subscribe to, and process real-time data feeds.

**Evolution of Kafka:**

* **From Message Alerting:** Initially, Kafka focused on delivering real-time alerts and notifications within LinkedIn.
    
* **To Stream Processing:** It expanded to handle continuous streams of data, enabling real-time analytics, fraud detection, and other applications.
    
* **Current Capabilities:** Now, Kafka offers a comprehensive platform for:
    
    * **Publish-subscribe messaging:** Efficiently sending and receiving messages between applications.
        
    * **Stream processing:** Real-time analysis of data streams for insights and actions.
        
    * **Event sourcing:** Capturing a complete history of data changes for audit trails and replaybility.
        
    * **Integration:** Connecting with various data sources and systems through Kafka Connect.
        

In layman's terms, think of it as a producer generating messages on certain topics, and consumers on the other side subscribing to these topics to exchange messages, forming a publish-subscribe model.

When we have a high load and our Kafka cluster is up, we need to manage all this traffic. We can easily scale our Kafka clusters by increasing the number of brokers to handle the load.

**<mark>Fault Tolerant</mark>**

If our broker goes down then our Kafka cluster can still get alive and continues to send messages due to something called Partition Replicas on other brokers. Thus, Kafka is Fault-Tolerant and very scalable.

# Updates to Kafka Infrastructure

The old model of Kafka as a messaging subscription service between the consumer and the producer has evolved into a new model. It has become a whole integrated ecosystem with a lot more tools like:

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716482184794/009e4a62-c850-4223-a3ef-858316fac5e1.png align="center")
    
* **The Consumer and producer API:** It create an application in Java for messaging service with easy of use.
    
* **Mirror Maker:** It mirror our Kafka from one data center to another data center.
    
* **Kafka Connect:** It move data from one Database to another database.
    
* **Streams API:** For relative processing of data, Kafka ingest the relevant data, filters and maps of data using Streams API.
    

## Kafka Topic

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1716482400271/a8da2583-c6df-4168-9523-89dcf7ff9987.png align="center")

Producers and consumers can communicate with each other with the help of these topics. Thus, we can think of them as commit logs where the producers publish messages onto these files or logs, and consumers consume them.

Topics are made up of partition through Kafka using <mark>Sharding</mark> in which we choose to have let's say three topics then those may have number of partition replicas which will be produced which helps in case we got any fault and act for **Fault Tolerance**.

# Kafka on Kubernetes

Kafka with kubernetes brings up a highly designed distributed and scalable message application. Even the operator workloads which comes with it are distributed and scalable so when it gets combined with Kubernetes, we get a great infrastructure and Cloud Native development.

Now it's pretty cool but using Kubernetes and Kafka both together and configuring them to set up Kafka on Kubernetes isn't easy at all as we also need to make sure that our Brokers are able to connect with each other and able to connect to consumers and brokers.

## Strimzi Contribution to Kafka

Strimzi is a CNCF sandbox Open Source project. It is a great operator for running Kafka on Kubernetes which is based on operator pattern where this operator has over business knowledge/logic.

So, **Strimzi** helps in deploying Kafka on Kubernetes by providing you Kubernetes Native experience as well by providing various resources like Kubernetes clusters, pods, replicaSets, daemon Sets, etcd and a lot more resources.

Strimzi provides you CRDs (Custom resource Developments) which can be used in addition to Kubernetes resources for the Kafka and other Kafka components. These CRDs can be provided to the operators to perform all the tasks for us and in this way <mark>CRDs are providing us the Native Experience</mark>.

## Built-in Security

Strimzi also provide us built-in security like producing TLS certificate and manage authentication or authorization of different types very very very easily!!

```bash
apiVersion: kafka.strimzi.io/v1beta2
kind: kafka
metdata: 
    name: my-cluster
spec: 
    kafka:
        version: 3.6.0
        replcia: 3
        likeness: 
            - name: tls
            port: 9093
            type: internal
```

## Kafka Custom Resource

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717836861690/8c5e4c82-9a5c-4a78-a8a1-e6148ba22260.jpeg align="center")

1. **Kafka**:
    
    * **CRD Name**: `Kafka`
        
    * **Purpose**: Defines a Kafka cluster configuration.
        
    * **Description**: This CRD allows you to specify the configuration for a Kafka cluster, including broker settings, Zookeeper settings, and other Kafka-specific configurations. It manages the lifecycle of Kafka brokers and Zookeeper nodes.
        
2. **Kafka Topic**:
    
    * **CRD Name**: `KafkaTopic`
        
    * **Purpose**: Manages Kafka topics.
        
    * **Description**: This CRD allows you to create, configure, and manage Kafka topics. It includes settings such as the number of partitions, replication factor, and configurations related to the topic.
        
3. **Kafka User**:
    
    * **CRD Name**: `KafkaUser`
        
    * **Purpose**: Manages Kafka users.
        
    * **Description**: This CRD handles the creation and management of Kafka users, including their authentication and authorization. It supports setting user quotas, permissions, and authentication mechanisms like TLS and SCRAM-SHA.
        
4. **Kafka Connect**:
    
    * **CRD Name**: `KafkaConnect`
        
    * **Purpose**: Manages Kafka Connect clusters.
        
    * **Description**: This CRD configures and manages Kafka Connect clusters, which are used for integrating Kafka with external systems. It allows you to specify connector configurations and manage the lifecycle of the Kafka Connect cluster.
        
5. **Kafka Bridge**:
    
    * **CRD Name**: `KafkaBridge`
        
    * **Purpose**: Provides HTTP-based access to Kafka.
        
    * **Description**: This CRD manages Kafka Bridge, which offers a RESTful API to interact with Kafka clusters. It is useful for applications that need to produce and consume messages over HTTP rather than using Kafka's native protocol.
        
6. **Kafka Mirror Maker**:
    
    * **CRD Name**: `KafkaMirrorMaker`
        
    * **Purpose**: Manages Kafka MirrorMaker instances.
        
    * **Description**: This CRD is used to configure and manage Kafka MirrorMaker, a tool for replicating data between Kafka clusters. It allows you to specify source and target clusters and configure replication settings.
        
7. **Kafka Mirror Maker 2 (Kafka mirror)**:
    
    * **CRD Name**: `KafkaMirrorMaker2`
        
    * **Purpose**: Manages Kafka MirrorMaker 2 instances.
        
    * **Description**: This CRD configures and manages Kafka MirrorMaker 2, an enhanced version of Kafka MirrorMaker. It supports more advanced features for data replication between Kafka clusters, including replication policies and more flexible configurations.
        
8. **Kafka Rebalance**:
    
    * **CRD Name**: `KafkaRebalance`
        
    * **Purpose**: Manages the rebalancing of Kafka cluster resources.
        
    * **Description**: This CRD is used to optimize the distribution of partitions and replicas across Kafka brokers to ensure balanced resource usage and improve performance. It automates the process of reassigning partitions and adjusting replica counts.
        

# Operators within Strimzi Architecture

## **Strimzi Architecture:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719369166874/a6adc8af-7501-4fed-9127-9b58f6d8bbd6.png align="center")

1. ### Cluster Operator
    

The Cluster Operator is responsible for managing Kafka clusters on Kubernetes. It ensures that the desired state of the Kafka cluster is maintained and handles tasks such as deploying Kafka brokers, ZooKeeper instances, and other related components. Once we have written our Kafka CRD and then provide it to the cluster operators based on their custom resource, cluster operator will deploy our Zookeeper pods, Kafka pods and another pod which is called Entity Operator. It performs various functions like:

1. **Cluster Creation**:
    
    * Reads the Kafka custom resource (CR) and deploys Kafka and ZooKeeper pods based on the specified configuration.
        
2. **Cluster Management**:
    
    * Ensures that the Kafka and ZooKeeper clusters remain in the desired state, even if there are changes in the configuration.
        
    * Handles rolling updates for Kafka and ZooKeeper to apply configuration changes without downtime.
        
3. **Scaling**:
    
    * Manages the scaling of Kafka brokers and ZooKeeper instances up or down based on changes in the Kafka CR.
        
4. **Monitoring and Metrics**:
    
    * Deploys and configures monitoring tools (e.g., Prometheus and Grafana) to collect and visualize metrics for Kafka and ZooKeeper.
        

**CRD:**

* The `Kafka` CRD is used to define a Kafka cluster, including its brokers, ZooKeeper instances, listeners, storage configurations, and more.
    

2. ### User Operator
    

The User Operator manages Kafka users within a Kafka cluster. It simplifies the process of creating, updating, and deleting Kafka users, as well as managing their authentication and authorization settings. It helps by performing various functions like:

1. **User Management**:
    
    * Creates, updates, and deletes Kafka users based on the `KafkaUser` CR.
        
2. **Authentication**:
    
    * Configures user authentication using mechanisms such as TLS client authentication and SASL SCRAM-SHA.
        
3. **Authorization**:
    
    * Manages user permissions, including ACLs (Access Control Lists) to control access to Kafka resources like topics and consumer groups.
        

**CRD**:

* The `KafkaUser` CRD is used to define Kafka users, their authentication credentials, and their permissions.
    

3. ### Topic Operator
    

The Topic Operator manages Kafka topics within a Kafka cluster. It automates the creation, updating, and deletion of topics, ensuring that the Kafka topics are always in sync with the Kubernetes custom resources. It's key functions include:

1. **Topic Management**:
    
    * Creates, updates, and deletes Kafka topics based on the `KafkaTopic` CR.
        
2. **Synchronization**:
    
    * Ensures that the Kafka topics are synchronized with the custom resources, reflecting any changes in the topic configuration.
        
3. **Validation**:
    
    * Validates topic configurations to ensure they meet Kafka requirements and best practices.
        

**CRD**:

* The `KafkaTopic` CRD is used to define Kafka topics, including their partitions, replication factor, and configurations.
    

Traditionally kafka was relied on Zookeeper for managing cluster metadata like topics, partitions, etc. Thus running two different systems together: Kakfka & Zookeeper.

## KRaft

KRaft which stands for Kafka Raft is a consensus protocol that replaces Zookeeper. It allows Kafka to manage its own metadata internally by simplifying architecture by eliminating the need for a separate systems and streamlining deployment. We can deploy KRaft on Kafka with Strimzi.

Strimzi and Kafka operator are tools that help automate Kafka deployments on Kubernetes which leverage KRaft mode by default, taking advantage of it's benefits for easier management and scalability within your Kubernetes environment. Once our cluster operator has deployed the ports for Zookeeper and our Kafka pods then this Entity operator container contains 2 pods as:

* User Operator
    
* Topic Operator
    

These two operators (User Operator and Topic Operator) are managed by a single Entity Operator container. So user operator manages user custom resources and topic operator will manage topic custom resource.

# Demo

Connect to our minikube cluster and have strimzi operator pod Up.

```bash
kubectl get pods n-n myproject
```

To view pods in our cluster we can deploy the operator, also we can use Helm Charts, yaml & Github.

```bash
kubectl cerate -f kafka.yaml -n myproject
```

Here kafka.yaml should be present already or may download the example file from somewhere else. To use Kafka custom resource where we are also using TLS authentication.

```bash
kubectl get pods -n myproject -w
```

Now here we will see our Zookeeper pods and then we will see our Kafka pods getting deployed which once these are in running state we are going to deploy the Entity operator pods.

Then we can see the viewing of our Kubernetes Cluster by some monitoring tools like Lens IDE, Prometheus, Grafana, DataDog, etc.

```bash
kubectl get kafka my-cluster -n myproject -o yaml
```

Now here this will check and show if our Kafka cluster is running.

Since, we are using TLS we will be creating some user, topics and then the application.

```bash
kubectl create -f topic.yaml -n myproject
```

To create topic for our strimzi kafka cluster.

```bash
kubectl create -f user.yaml -n myproject
```

To create user with certain information like the authentication is of type TLS and various other information.

```bash
kubectl get secret my-user -n myproject
```

To create secret in our cluster.

```bash
kubectl get secret my-user -n myproject -o yaml
```

To get it in more collaborated form.

Now the next step is to deploy the consumer.

```bash
kubectl create -f consumer.yaml -n myproject
```

To create consumer.yaml and consumer is going to be of deployment type.

```bash
kubectl get pods -n myproject
```

Now here in the Kubernetes dashboard, we will see the consumer subscribed to the topic and in the same way once this happen, we can also create the producer. Then the producer is going to produce messages which will be consumed by the consumers.

```bash
kubectl create -f hello-world.yaml -n myproject
```

To create the hello-world.yaml

Now we just saw how TLS works with Strimzi but it has a lot more features like Configuration, Scale down, Scale up, Toleration, Metrics, Affinity, Authorization, HealthChecks, Zookeeper, Topics, Source2Image, Storage, JVM configuration, multiple storage, kafka Connect, User, CPU & RAM, Mirroring, Pod Disruption Budgets, Oauth, HA, Configuration, Labels, Cruise Control, Secrets, Upgrades, Off Cluster access, ACLs, HTTP Bridge, ImagePullRequests, Grafana, Prometheus.

**<mark>Strimzi Friends</mark>**

Apart from features we do have a lot of CNCF project integrations like:

* Helm Charts
    
* Jaeger
    
* Keda
    
* Fluentd
    
* OpenTelemetry
    
* Open Policy Agent
    
* Prometheus
    
* Kubernetes
    

I hope you get to learn something new from this blog which introduced amazing topics like Kafka and Strimzi to your knowledge bucket😄. Soon, I will be releasing a video about Strimzi and Kafka with good use cases and Strimzi usage on my Youtube channel. If you wish to enjoy such videos on such a massively increased required tool like Kafka then here is my Youtube Channel 😄

%[https://www.youtube.com/channel/UCPukGLZnjiMnPdDOFwZWV_A] 

Soon, i will be releasing more blogs and videos on such CNCF Landscape projects, tools, services and platforms, as the list is huge so we haev to get going with the flow 😄 because we all know:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719409217698/5b18242e-b911-4ce5-b906-6e7803ae2284.jpeg align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)