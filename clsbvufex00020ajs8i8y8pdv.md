---
title: "Web Assembly: Evolution to Containers 📦"
seoTitle: "Web Assembly: Evolution to Containers 📦"
seoDescription: "In a world where the web is evolving faster than ever, imagine a technology that brings the performance of native applications to the browser."
datePublished: Wed Feb 07 2024 14:26:07 GMT+0000 (Coordinated Universal Time)
cuid: clsbvufex00020ajs8i8y8pdv
slug: web-assembly-evolution-to-containers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707314047627/fc4cdd57-d8d0-4174-8e91-707480eed068.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707315871654/b9b9cdb0-5a6e-45ce-a46e-dd26172194ee.jpeg
tags: cloud, docker, security, webassembly, kubernetes, cloud-computing, devops

---

In a world where the web is evolving faster than ever, imagine a technology that brings the performance of native applications to the browser. Welcome to the realm of Web Assembly, where the boundaries between web and native are blurred, unlocking unprecedented possibilities for developers and users alike at native speed.

Web Assembly defines a portable, size and load-time-efficiency format, execution model specifically designed to serve as a compilation target for the web. It is a compilation target, so there exist a universal bit code that our code/program compiles to which can run on any platform or machine.

It is summation of a lot of approaches and efforts tried earlier to make such kind projects to run on any browser, but those were very language-specific and not language-agnostic like Java, applets, Adobe Flash, VB script. On the other hand, today Web-Assembly is a massive ecosystem with a specific landscape in CNCF.

It is a joint effort result by a lot of big companies coming together and putting efforts together formulating to make it universal. Although it becomes interesting when it get added as the fourth language of Web after HTML, CSS and JavaScript.

The core difference came up with it's focus on being language-agnostic Binary-format instead of being language-specific like Java applet. So, it's a language-agnostic compilation target which when compiled to wasm which is a wasm module or wasm component and now we will be able to run it on any platform where we will be having web assembly runtime.

# WASM v/s JVM

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707314229691/1c4b3b4d-0133-43e7-9b24-bd6b7c9c1d50.jpeg align="center")

So we already know whatever code we write, get converted to machine code as CPU can only understand machine code. These machine code are binary numbers or CPU instruction which comes as operation code which tells what does a CPU needs to do.

Slowly, it started to getting very difficult for the developers and vendors to write code in Assembly language with different CPU architecture. Here's where the Virtual Machine code came into existence which helps in abstracting their code and resisting re-writing of code by developers and vendors. This is what JSM was with Virtual Machine code which was language specific as it was only specific with Java on the other hand WASM in language-agnostic.

# Strict Sandboxing

### Sandboxing

Sandbox in general is a contributed environment where our code executes without effecting the rest of the program, for example whatever has been taught in one class is not related and does not effect the things taught in some other class of different subject in the same building and thus, that building is a sandbox.

Now, as we know Web Assembly runs on a universal Binary code format so, when web assembly runtime is running the code so the run time is making sure that the web assembly code is running isolated from the host runtime which shows that the module execution and your host runtime are separate.

It executes with WASM providing a secure environment to run your code inside the browser. WASM doesn't directly touch our system instead it pick web API to perform it also it has a separate memory buffer to keep it away from other applications which act as a separate isolated memory.

There are specific checks that the browser check for WASM code to resist any security pitfalls, policies ensure that WASM modules respect the website boundaries. Modern browsers have built-in protection to further shields against it, which ensures that it is sandbox and you can't access anything outside the browser or even if we are running Web Assembly or server-side, we need specific philosophies like WASI (Web Assembly System Interface) to access any particular resource explicitly. We do have a shared pool and multiple web-assembly modules which are consuming it, then becomes very hard to maintain the security level, the WASM and runtime implementation which makes everything possible that is written in specifications of Web Assembly.

Runtime makes it probably possible and makes the secure sandboxing as the strict sand boxing where our code is running with secrets and important details on browser which can be compromised and due to malicious activities which won't effect your overall systems as it doesn't have any resources required with respect to your host thus, it will be running isolated and securely. Thus WASM has secure sandboxing which isn't present with the JVM.

# Web Assembly success in Browser

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707314340534/7d81464b-75af-4eb8-9864-4a47839a0d4c.png align="center")

Efforts were being made earlier to make their application accessible on web browser by everyone as the traffic and engagement of people on web browser increased exponentially which is being continued even till now. While it was happening everyone wants to deploy their application to browser but they were written in traditional language like C, C++, Java, Golang, Rust, etc.

So Adobe and many other companies have used tools like M Script which is a tool chain to convert the LLM IT to Web Assembly where M script has been instrumental in demonstrating the potential of Web Assembly and helping the transition of full application or part of them to run inside the web browser.

Then we had Figma which had asm.js and ported to Web Assembly when talking of successful browser application then these 2 application comes instantly to the mind for designing web templates in figma and adobe photoshop for editing with instant drawing and applying on web with speed compared with smoothness means near native speed.

### Near-Native Speed

Thus, Web Assembly gives you the near native speed with the application being produced in the native languages like C, C++, java, Golang, Rust, etc, and deploy your code or different parts of code on browser to compile with that performance tuning set in our languages.

It holds such high powers due to it's smoothness provided with applications in their adopted languages. Google Earth collaborates with Web Assembly and the 3D format for smoothness due to the assembly formation modules that are running over there. Multiple Online gaming also include their infrastructure being built with Web Assembly to allow smooth graphics and quick functions with online collaboration with your teammates.

***<mark>Web Assembly is write once run anywhere.</mark>***

## Web Assembly Features

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707314959627/137efcfc-220d-490b-9e86-e951ac9f5d74.png align="center")

Compiling to different architecture isn't that difficult as it could be performed with different tools, but the real power of Web Assembly lies in:

* Secure sandbox running at native speed
    
* Programming in our chosen language then compile it to web assembly, run and then ship it.
    
* The smaller binaries, as it isn't like Docker where all the dependencies and libraries are also packed up in the containers. Thus we can straight away deploy our code in the smaller binaries which can be executed by other in their own application.
    

Although JVM also comes with similar features but, it is language-specific to Java and not language-agnostic like Web Assembly, also it doesn't have accepted by w3c standards which pushes it much behind Web Assembly in the league.

features provided by the Web Assembly are:

* Isolation & Security
    
* Multi-Platform
    
* Smaller Binaries
    
* Instantaneous Startup times
    

These were used by the applications for porting to web with Web Assembly although as we can see the following things are required everywhere and thatswhy, a huge potential was starting to gain popularity in Web Assembly ecosystem for the server side as, these have requirement at the server side giving rise to the new concept for Web Assembly ecosystem.

# Evolution Waves

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707314670749/0b435ffe-2c0e-40b4-95cb-7f30ecd642e2.jpeg align="center")

Firstly, servers were hosted by companies to deploy their applications to the browser, later Virtual Machines came where we can get connected to the virtual servers with one click.

Then containers came with more abstractions where we can abstract and package our application with code, dependencies and libraries and then run our application with any required number of containers.

Web Assembly got more abstracted than even containers where it doesn't have to hold the dependencies and libraries in the package and deploy our code straight away to the containers and docker as it doesn't have any relation with the host of the operating system, then the code can later be used by any other person who extracted our code and thus can be used in their application and code base as a component.

Specific permissions explicitly are required in advance to give access to major tool chains like wazi. Thus, it's deny by default and explicit permission required to offer access.

## Serverless application & instantaneous startup time benefits

It is highly beneficial for serverless application, edge use cases for edge applications with very lesser memory and still have assembly runtime which can run our web assembly modules on these devices and start up times are instantaneous powering the next generation serverless. Thus many startups in Web Assembly are able to provide next generation serverless service based on web assembly, which puts them ahead of any other service with such high native speed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707314849204/8ad1f571-b28f-4c4d-94ab-7a3da7fa311c.png align="center")

So, here we had our code in Go which got converted using tool chain **chargo** to build and target **wasm32-wasi** to build the executable file, where **hello.wasm** is platform-agnostic which is able to run on any architecture with web assembly runtime so that, we would have a JavaScript equivalent code, which when compiled using the tooling would be able to run on any architecture using Web Assembly run.

We have seen hwo these features of faster runtime, secure sandboxing, near native speed and language-agnostic are imported for server but, not as easy for server side with Web Assembly. Web Assembly at server side is being discussed since the success of Web Assembly at browser which is really useful where high computation is required such as with case of:

1. inferencing Use Cases
    
2. Image Processing
    
3. Simulations
    
4. Secure Sandboxing
    
5. Game Server
    
6. Near Native Speed
    
7. Platform Agnostic
    
8. Portable
    

Although we do have some interesting use cases of Web Assembly already existing at server side at production as:

**<mark>Cloudfare Workers</mark>**

Cloudfare Workers allows Web Assembly running at edge bringing the computation closer to user. With Cloudflare Workers, developers can execute code closer to the end-user, reducing latency and improving performance.

**<mark>Fastly</mark>**

Fastly computes at edge utilizes the web assembly for the serverless function. Fastly's support for Web Assembly empowers developers to build and deploy lightweight, highly performant serverless applications that can be executed close to end-users.

**<mark>Fermyon</mark>**

Fermyon which uses web assembly to power the serverless. With Web Assembly, Fermyon can achieve high performance and scalability, making it suitable for a wide range of use cases, from web applications to IoT devices.

**<mark>Shopify</mark>**

Shopify for frontend & backend dashboard and also uses web assembly for image manipulation data processing for enhancing their efficiency, which is crucial for providing a seamless user experience in e-commerce applications. Web Assembly allows Shopify to execute compute-intensive tasks efficiently, leveraging the performance benefits of compiled code while maintaining portability across different platforms.

# Difficulties with Web Assembly

When we talk about WASM on the server side then we need to do some interaction with host, interact with files by writing, reading directories environment variables. These are some of the common things you need for any application to run on server side.

We already know that Web Assembly don't know about host, keeping secure sandboxing in place. Thus, in 2009 Web Assembly System Interface (WASI) proposal was adopted whose implementation are done by Web Assembly runtime so when you install it, we can use WASI or our application to interact with host operating systems to do tasks like accessing the environment variable files and directories keeping secure sandboxing in mind as we provide very specific access via WASI to access in secure way.

## WASI & Component Model

### WASI

Major tags and features that were focused in the earlier time of Web Assembly adaptation at server side were security and portability to make sure Web Assembly could be used outside the browser as well. Whenever we do an application call then it goes via the kernel as cis calls which then access the file system which in Web Assembly ahs to be done using WASM module which doesn't compile to a specific Operating System.

### Component Model

With Web Assembly, we can write code in any language so let's say we wrote code and then exported our code, then the another person can import can import it which will help in removing duplicacy and also will help in code re-usability as here, we would be able to use someone else component that does a specific functionality in our own code base by importing that component of functionality in your application. Thus, it helps in code re-usability and language neutral plugins.

# CNCF WASM Landscape - Bytecode Alliance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707315037538/340b51d7-e507-412c-afc3-abb9697a646b.jpeg align="center")

Bytecode alliance is a non-profit organization dedicated to creating secure New Foundation building on standards such as Web Assembly and WASM (Web Assembly System Interface). It is also establishing a capable secure platform that allows developers and service providers to confidently run untrusted code on infrastructure Open Source devices.

Thus, it is the foundation for Web Assembly ecosystem, certain organization like Amazon, Cisco, Anaconda, arm, candle and cosmonic are working towards the standardization of Web Assembly projects. There have been many projects adopted in Bit code Alliance like Wasmtime, Cranelift, WAMR and Javy to maintain the security and the sandboxing for the Web Assembly projects.

Byte Alliance have TOC and have been putting efforts for team discussion, team formation form different organization who are working in the Web Assembly ecosystem on different runtime, who are collaborating on all **w3c** standards with respect to Web Assembly on component model of WASI ecosystem on the AI inferterfacing standardization and are trying with the same foundation so that everyone agrees. Byte Code is same as what CNCF is for Kubernetes.

---

In case, you want to get in-depth knowledge about the Web Assembly, it's use cases, hands-on practice, future predictions and how big it can impact the domain then head on to the amazing course by @[Saiyam Pathak](@Saiyampathak) on his Youtube channel KubeSimplify, where he regularly publish videos and content on amazing projects, platforms and services on CloudNative, Kubernetes, DevOps, Platform Engineering and many other tech stacks for better observability, scalability, security, monitoring, AI-LLMs and sustainability.

Web Assembly Course by KubeSimplify: [https://www.youtube.com/watch?v=eYekV2Do0YU&t=1s](https://www.youtube.com/watch?v=eYekV2Do0YU&t=1s)

KubeSimplify Youtube Channel: [https://www.youtube.com/@kubesimplify](https://www.youtube.com/@kubesimplify)

Hope you get to know about this game changing tool which is gathering a lot of popularity due to it's high security feature, language-agnostic and smaller binaries features. Soon, I will be releasing more blogs with in-depth information about Web Assembly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707315797896/18799360-0a5e-4dc4-8960-d6cc92e82e83.jpeg align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)