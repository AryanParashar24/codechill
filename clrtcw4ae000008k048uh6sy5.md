---
title: "Lens Autopilot: Reduce Risk & Liabilities with Kubernetes☸️& Platform-as-a-Service for CNCF Landscape"
seoTitle: "Lens Autopilot: Reduce Risk & Liabilities with Kubernetes☸️"
seoDescription: "We will be discussing how to reduce risks & liabilities in Kubernetes with Lens Autopilot & recover some ideas around security for a better security posture"
datePublished: Thu Jan 25 2024 15:15:42 GMT+0000 (Coordinated Universal Time)
cuid: clrtcw4ae000008k048uh6sy5
slug: lens-autopilot-reduce-risk-liabilities-with-kubernetes-platform-as-a-service-for-cncf-landscape
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706180451964/e40c8452-75c2-4013-aea7-33994b9a25e7.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1706195626078/cfb80f78-53f4-471a-bca4-ef6efe994b0e.jpeg
tags: software-development, security, software-architecture, kubernetes, devops

---

We will be discussing how to reduce risks and liabilities in Kubernetes with Lens Autopilot and recover some ideas around security for a better security posture for our Kubernetes clusters through better observability within a given cluster and how Mirantis have been collaborating with CNCF to boost up the customer experience with better Security infrastructure through Lens Autopilot.

Lens allows you to connect and interact with multiple cluster with all resource like deployments, objects, ReplicaSets, Networking Security, etc.

We can also share our Kubernetes clusters without having to share our kube-config files, which will resist any breach of data or secrets and contribute in increasing security of our containers.

One of the main feature of Lens is that it allows the development within our container locally which is allowed by the feature called Lens-Development-Kit (LDK).

# Understanding Security Vulnerabilities

Now, within our cluster we can browse through the workloads and look for our application which is deployed in our cluster through the Network section in sidebar and look for it in the Service section where we can select our application and copy-paste our external IPs to our local browser where we will be able to see the application up and running in our cluster through the browser.

The main problem which the normal approach is that, we can't really look into the vulnerabilities in the pod, configuration or the different configuration being used which might cause damage in future, neither we do have any visibility of events like connecting to pods towards kubeAPI.

# Attack History and Impact

This blog is going to be published by 26 January 2024 and just 2 days ago, tech industry experienced the biggest data breach of about 26 Billion records getting exposed through the platforms like Facebook, Google, twitter, Dropbox, Snapchat, Linkedin and many other platforms.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706189344115/f65ccdb3-0aa0-49ef-b0b0-079fc485b8f2.jpeg align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706189360309/0460efde-2574-4864-8cbc-a0ad40d09fec.jpeg align="center")

There have been many Ransomeware Attacks on many projects of major companies as well like as submitted by BlackFog identified total of 376 Ransomeware attacks with different impacted countries with departments related to different fields like IT, education, medical, government sites and organizations, power producing plants and sites, etc with a direct impact of nearly $457 Million USD which is comparatively much much much lesser compared to 2021 with an impact of huge $ 6 Trillion, even higher than $ 3 Trillion USD in 2015.

Indirect impact included shutting down of small business/ production of data and security threats for a lot of people effecting company's trust and reputation in the eyes of partners, users and customers.

### Common Threat Detected

It was seen that about 53% of all the effected systems had 1 critical vulnerabilities exposed to the internet which had 800,000 of them with 1 exposed vulnerability. Over 1000 vulnerabilities were exposed to the internet by 22% of services and systems. The average time to remediate and fix these CVEs stood between 270 to 426 days which is quite time consuming which won't be able to hold trust with companies' users and partners.

### Measures to consider:

You should be able to choose our CNI, CSI, CRI or any other features to apply any specific security policies or need to be able to work with a partner and influence that choice.

You should be able to choose the operating system we decide to run your workloads and not to get forced into one given operating system. We should adopt an Onion infrastructure which have multiple layers although it has started from a single core and we will have to assure the core's security like in any Kubernetes workloads, the core is our runtime and thus it should be highly secured.

# Building Security Supply-Chains as a Solution

Working with trusted partners which can help you fix issues much quicker on specific layers of your application, which can be libraries we are using for operating system can bring up as a solution to identifying and start working onto their solutions for security vulnerabilities. Delegate trusted partners will help you fixing issues so that we can concentrate on building and fixing your code with tooling available which will fix your code as early as possible.

It will help in building a secure supple chain which is mandatory when industrializing everything in the later parts.

## Secure Supply Chains components

Secure supply chain is a combination of three ways:

* Runtime
    
* Registry
    
* Kubernetes Clusters
    

**Runtime:**

The runtime refers to the environment where your applications run. Techniques like runtime security scanning can be employed to continuously monitor and analyze the behavior of containers during execution. This helps in detecting any anomalies or security threats in real-time.

**Registry:**

The container registry is a central repository for storing and managing container images like DockerHub. Securing the registry involves implementing measures such as image signing, which ensures that the images are authentic and have not been tampered with. Digital signatures are used to verify the integrity and authenticity of container images before deployment.

**Kubernetes Clusters:**

Kubernetes RBAC (Role-Based Access Control) helps manage privileges within the cluster. This ensures that only authorized entities have the necessary permissions to interact with the cluster resources. Admission controllers in Kubernetes can be configured to enforce policies and security checks before admitting pods to the cluster. For example, you can use admission controllers to ensure that only signed images are allowed to be deployed.

These three are mandatory to manage the privileges in our clusters and also to sign and scan these images to make sure that only signed images are allowed to run within our clusters.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706189243505/b7790759-3634-4598-82fc-108d2d20c9ef.png align="center")

Above is the illustration of how the supply chain would be built by an engineer, pushing a signed image to a registry will scan and promote the image so that Kubernetes cluster can run only signed images.

# Core of Kubernetes Security

Observability is the core of the Kubernetes Security which can help in reducing. As we were earlier trying to access the application we deployed in our cluster where we were unable to access the secrets, security issues, image scan status, outback rules and configurations. So, for security measures we need proper observation, dashboard provided by proper tooling.

Operation excellence depends on getting remediate as early as possible. It works on the fact that we have different configuration on staging environment as close as possible with production environment which will give much faster solution and observation to the security issues to get results solved quickly and work on them closely on the production environment.

**This is handled by Lens AutoPilot.**

# Lens AutoPilot

Lens Autopilot is a Zero-Ops platform which addresses two things: Choice & Skills.

Lens Autopilot provides skilled DevOps engineering staff and various Open Source and partner tooling to speed up the process of development cycle by speeding up the delivery process so that developers can focus on their core application and getting it deployed and ignore worrying about the production of tools for security and management which will eventually increase user-experience.

Lens Autopilot provide 24x7 support and can access Lens's experienced DevOps experts during time frame, proactive security and it's enterprise Scalability to scale out to the multiple clusters.

### GitHub adaptation:

Lens Autopilot is leveraged by GitHub approach as through GitHub approach we got continuous updates, upgrades of the components and thus Lens Autopilot takes care of all of these continuous features and consuming the resource provided.

* It provides choice to choose any infrastructure and environment, let it be VMware, Tanzu, AWS, Azure, Google Kubernetes Engine (GKE), OpenShift or even Mirantise Kubernetes Engine.
    
* We can choose any Linux distribution like Oracle, Enterprise Linux, Rocky Linux and at the end we are also left with the choice of Kubernetes like EKS, AKS, Tanzu or OpenShift, we have capabilities to use any of your available Kubernetes clusters.
    
* GitHub will come in for various tasks like monitoring, logging, analytics, networking, CI/CD and they also have add-ons as well.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706193677135/c0b369f0-747c-46a5-90a7-80caab1a89ec.png align="center")

1. Lens AutoPilot has the first element for managing the access to the environment, for example we are deploying Keyclock and we are managing it so we can either use it as main identity-provider with it's OIDC adaption or we would be connecting Keyclock to an external provider to federate, to act as a broker to access the cluster to amnage authentication and authorization of users to access our clusters.
    
2. Second element we would be deploying is OPA gateway through where different rules will be defined through where different rules will be defined by us and we would be able to manage the access control of different objects within the clusters.
    
3. Third element we would be deploying is set of components that is provided through Aqua like through Aqua kube-bench, Aqua kube-hunter and Aqua Stanboard which are different components to allow us to scan different images and would allow us to get access to the different security configurations of throughputs and will also have access to different images and configure it to cluster scope or object scope. We will also have access to node configuration and security configuration for these different nodes for building our clusters.
    
    * **Aqua kube-bench:** Aqua Kube-bench helps in identifying and rectifying potential security vulnerabilities, ensuring that your Kubernetes deployment adheres to industry-standard security benchmarks. This is crucial for protecting sensitive data and ensuring compliance with security standards.
        
    * **Aqua kube-armour:** Kube-armor helps in detecting and preventing security threats during the execution of applications in the cluster. This adds an additional layer of defense, making the overall Kubernetes environment more robust and resilient.
        
    * **Aqua kube-stanboard:** Aqua Starboard provides a centralized view of security-related information, making it easier to identify potential risks and take proactive measures. This contributes to improved overall security management and compliance.
        
4. Then we have Falco, which is use to monitor the different events within our system and Kubernetes so we can see the system events and Kubernetes events like we can set to observe which container are talking to kube-API or defining/setting a rule within file.
    
5. Then we have App via crane which allow us to have a proper visibility of our back configuration and thus understand what accessibility is been distributed to whom in the network in a much easier manner.
    
6. We also use Goldilocks for logging which allows and help us in giving us recommendations of how much resources should be used by your application so that at some point if they are attacked then your cost won't be exploited by these pods contained within these set limits.
    
7. Trilio, a partner of Mirantis which allow us to backup and recover in case of disaster rewrite, so in case we have that bridge and need to re-deploy our services in another cluster by reloading our data, then Trilio will be helpful in tha case.
    
8. Sysdig, another partner of Mirantis which provides enterprise support for Falco with an extra capability through their systematic secure accessory.
    

# CNCF Landscape integration for Security

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706195043085/d3466e79-06a9-4d2a-97ae-582ef570ed43.png align="center")

Lens Autopilot provide the collaboration a lot of CNCF Landscape projects as stated earlier like Aqua, kube-Armo, Aicide, Synk, Sysdig, Trivy, etc. We do know we have more capabilities in CNCF Landscape, so if we don not want to work with those then Lens AutoPilot adopt the Platform-as-a-Service (PaaS) whcih is an extension of Lens AutoPilot to perform custom integrations with specific components, we want like for Security, logging, monitoring, CI/CD and what not thus it can have them integrated within the cluster.

**Extension of Lens AutoPilot with** the adoption of Platform-as-a-Service (PaaS) within Lens AutoPilot allows users to perform custom integrations tailored to their specific requirements. This flexibility is crucial, as different organizations may have unique needs in terms of security, logging, monitoring, CI/CD, and other aspects of cluster management.

By adopting PaaS, users can seamlessly integrate their preferred components or tools for various purposes, such as enhancing security measures, optimizing logging strategies, and streamlining CI/CD pipelines. This ensures that Lens AutoPilot remains adaptable to diverse use cases and can be tailored to the specific requirements of different environments.

Hope you have got some information added to your knowledge and got some more security tooling choices for your application, soon I will be posting more in-depth information about the Lens Autopilot and many other CNCF landscape tools and applications until then keep grinding🔥.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706196957304/61defcc4-4691-47ea-bf85-d1315f6e186e.gif align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)