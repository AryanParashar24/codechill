---
title: "Docker Basics & Architecture"
seoTitle: "Docker Basics & Architecture"
datePublished: Sun Apr 16 2023 19:54:27 GMT+0000 (Coordinated Universal Time)
cuid: clgjtso6n000309lc6dll7ddn
slug: docker-basics-architecture
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681488205916/187ea570-8164-43f5-9444-563095a67f41.gif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1681613483502/3ba754e0-0732-416e-b490-510b351fc3b4.gif
tags: docker, technology, cloud-computing, devops, wemakedevs

---

Docker is a containerization platform that allows you to package and deploy applications as lightweight, portable containers. Docker is a set of platforms a service product that uses OS-level virtualization to deliver software in packages called containers.

It is all general knowledge and basic definition on the internet about Docker, but let's see how tech works and why we need it in general.

# **Why was it Invented?**

Many years earlier, companies use to run their applications on servers which use allow the use of a whole server for a single application, which was a major problem economically as well as for the environment as well.

### Entry of VMWare!

This major problem was solved by VMWare which introduced Virtual Machines which solved the problem by allowing multiple applications on a single server or system by installing Virtual Machines on the same system which works by dedicating a considerable amount of RAM to the Virtual Machines.

This gathered a lot of attention in the tech world but gradually, there felt a requirement for some other substitute as developers and companies felt that for running their applications and for their use there should be a tech that could reduce the amount of size or RAM wastage and something that could be flexible or possibly able to increase and decrease the memory it's gathering based on

the

data present in the system. Many developers found out that if they need to work with data of only 2GB and in the starting while installing Virtual Machines on their system they provided let's say 10GB of RAM so 8GB of RAM is simply wasted untill it isn't filled out completely and to solve this problem comes into the play - Docker.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681672132206/3cf634f2-ca8f-4a6f-b1eb-15df5d53aa7e.jpeg align="center")

# All about Docker

## How does it work?

Docker is a containerization platform that allows us to build, test and deploy applications at a much faster rate. It deploys applications as lightweight in the form of portable containers. These containers are a lightweight executable package of software that contains everything needed to run an application- code, runtime, system tools, system libraries, settings, etc.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681671996997/736fb83c-0177-48fd-a8ae-1d73736c6a67.gif align="center")

A general modern-day problem that can be encountered for which Docker is preferred a lot over VMWare is let's say we decided to share an application with one of our friends or colleague to test it out or review it then, at many times we find out that the other person is facing a major problem that the app isn't running on his system due to some system permissions or application version or some other difficulty, So to get rid of this problem we use Docker.

# Components

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681672029108/9e2204d0-061d-4ab4-8faf-5bd14cb91a9e.jpeg align="center")

## 1) Runtime

It consists of two parts

* Run C
    
* Container d
    

**Run C**

Run C is like a low-level runtime responsible for starting /stopping of program

**Container d**

Container d is responsible for all other tasks like managing our containers, installing data from the internet into your containers, etc.

## 2) Docker Engine

It has various components based on which it fully operates.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681672232614/309e67ba-36b0-4398-a735-494e14cbfdce.png align="center")

All requests are been made by **Rest API** to the Docker Dameon.

While **Docker CLI** is where we write commands and interact with the command line, server and application.

**Docker CLI** will leave the request to **Rest API** where **API** will ask **Dameon** to give their command to **Docker Runtime** to go on with the tasks of RunC and Container d. The daemon creates and manages Docker objects, such as images, containers, networks, and volumes.

## Docker Engine

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681672405248/7e9e7858-3e60-4e54-aa88-e71aa90b7be4.jpeg align="center")

So making of the container is managed by Run C when we created an image and then send it to Run to create a container out of it.

Daemon talks to container d over APIs and crud over GRPC(gRPC is a modern open-source high-performance Remote Procedure Call (RPC) framework that can run in any environment. It can efficiently connect services in and across data centers with pluggable support for load balancing, tracing, health checking and authentication.)

So as according to the architecture there could have been a possibility as if, Dameon has to be updated or go through any other amendment then all the containers have to be stopped working as well which isn't a good idea so despite, RunC being removed from Container D once the container is created out of it and then after separation, Shim takes over and talk to ContainerD regarding creation, managing, etc.

Hence, the RunC is known as Dameonless containers as they continue to run even after the Dameon is down.

## Open Container Initiative (OCI)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681672349951/0d4b7838-8bde-4a3b-8029-26ad6e90486a.png align="center")

Open Container Initiative which was developed to get tackle the problems faced while working with Virtual Machines is a Linux Foundation Project at the moment which was originally developed by Docker in 2015 to initiate and design open standards for operating-system-level virtualization. It was then later given to CNCF (Cloud Native Computing Foundation).

## 3) Orchestrators

Orchestration is a very important component that is responsible for the automated configuring, coordinating, and managing of computer systems and software.

It runs in a structured way consisting of various parts as

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681672471132/89c03e10-02db-48d6-854a-6fb591bc7a57.jpeg align="center")

### Docker File

A Dockerfile is a script that contains instructions about how to build a Docker Image. It's a text document that a user could call on the command line to assemble an image.

To know more about how the docker file is created, you can head up to my other blog where I discussed all the steps of creating a dockerfile and the precautions to be taken while creating a dockerfile.

%[https://codechill.hashnode.dev/docker-image-generation-deep-dive-precautions] 

### Docker Images

An image is a snapshot of a container that includes all of the files and settings needed to run an application. When you build an image from a Docker File, Docker takes all of the instructions in the file and creates an image based on the instruction. It is a template that defines the environment and dependencies needed to run an application.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681672631556/ea3eb027-f822-4daa-b161-485779b1564a.jpeg align="center")

Once you have a Docker image you can create Docker Container out of it.

### Containers

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681672646163/df3a939c-1764-4787-b7a3-01be7678db3f.jpeg align="center")

The container is an instance of an image that is running as a process. Combined with DockerFile and Docker Image they allow you to create packages, and run applications in a consistent and repeatable way, regardless of the underlying system.

# Terminal Command line of Docker

```bash
docker run -it ubuntu
```

To run the mentioned image in the command to run the container out of it. As we write the command then our client will request Daemon.

The Daemon will look for the file/image we asked for in our local system, in case it isn't available in the local system then the Daemon will go to the **Docker hub registry** where people share their images and then, Daemon will download the image from internet and build up a container out of it.

it will download the latest version of the image or the application u r requesting to get downloaded onto your system but if u want to download a specific one then specify as-

```bash
docker run -it ubuntu:16.04
```

To upload your images from your local system to the docker hub u can register your free account and then link it with your terminal Command line u can run

```bash
docker login
```

And

```bash
docker build
```

To build a Docker image from a Docker File and get stored in your root directory as it is having "." in the end which could be changed for sure by specifying a path.

This feature of docker to use images that are not available on your system is very beneficial as it allows you to use and run some applications without even downloading them into your system.

Now one of the major questions that arise here is, that we already know that in the case of Virtual Machines being isolated from the main system that means that there will be no interference or relation between the main system and Virtual Machines.

**So doesn't it applies here in docker as well?**

Yes, here in Docker when the files or images are downloaded from the docker hub then along with the main file/image some other binary libraries are also installed into the system.

**One of the most interesting features it provides** is that when a file/image is installed by docker along which certain required binary libraries and files are also installed, and then later if we try to pull another image that requires one or more of the same binary libraries that were installed earlier then despite downloading them all again and again it points out to those files and skips their downloading hence saving up a lot of memory.

This is performed by downloading the whole file in the form of layers to check the availability of files in the system.

```bash
docker ps
```

It will list all docker functions running at the moment

```bash
docker stop <port_id>
```

Will stop the listed function from running at the moment whose port number we entered.

```bash
docker ps -a
```

To show all the functions running at the moment as well those which got stopped.

```bash
docker images -q --no-trunc
```

It will give the **Hash Value** of all the images and we will notice that **Image ID** is just a few starting letters of the **Hash ID** which could be noticed when we write the code

```bash
docker image
```

Will give IDs of all four image layers. Here we will be able to see that the files are distributed in these layers and the downloading processes of the already existing files are being jumped/skipped to reduce the memory engaged by these repeatedly downloaded files.

A whole dedicated blog for the terminal Command line and features will be noted in the next blog so just keep ur fingers crossed 🤞 to get that blog ready within a week😃😄

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681674766830/0cf11725-4894-448f-91f2-a9234e58ae53.gif align="center")

Thanks for reading! I hope you found this introduction to Go helpful and informative. If you have any questions or comments, feel free to reach out to me on Twitter:

My Twitter Profile: [Aryan\_2407](https://twitter.com/Aryan_2407)

I'm always happy to connect with fellow tech enthusiasts and answer any questions you may have. Don't forget to follow me for more updates on tech, programming, and more.😄😄