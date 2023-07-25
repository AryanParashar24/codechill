---
title: "Docker Image generation Deep-dive  & precautions"
seoTitle: "Docker Image generation Deep-dive  & precautions"
seoDescription: "Talkin about the Image generation and precautions that are needed to be taken while building an image"
datePublished: Thu Jun 15 2023 09:24:38 GMT+0000 (Coordinated Universal Time)
cuid: cliwxpui4001009jvhoxgb1bq
slug: docker-image-generation-deep-dive-precautions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686800491008/74fe543d-43f1-4934-a6ca-9ddeff70a770.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1686820993662/e1f7d911-3dff-4d78-9ad7-383e02a7ea59.jpeg
tags: docker, programming, technology, devops, 2articles1week

---

# What is Dockerfile?

Dockerfile is a list of instructions and rules to be followed by the Docker Daemon to build a container image.

(In case you don't know about Docker Daemon, container, images and basics of Docker reach out to my earlier blog on Docker for a complete beginner.

%[https://codechill.hashnode.dev/docker-basics-architecture] 

)

# Dockerfile Instructions

Dockerfile Instructions are the set of words conventionally written in the upper case in order to perform a specific action to your Image.

**For commenting "#" is used which is ignored by the docker while performing actions**

## List of Dockerfile Instructions

1. **From**
    
    ```bash
    FROM <Image_Name>
    ```
    
    It is the starting line in your Dockerfile telling out the base image &lt;Image\_Name&gt; on which our Image is based upon. Say for example we have a javascript application with node.js in the backend in the container, so to run over node application. Instead of basing it on some other low-level language like Linux where we will have to manually download node.js first by ourselves.
    
    In case we don't have it we can download it from DockerHub:--
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686802029699/9bfe301d-4b1b-4e83-b4c4-8d85c5d1739f.png align="center")
    

by writing code in the terminal as:--

```bash
docker pull node
```

1. **Env**
    
    ```bash
    Env MONGO_DB_USERNAME = admin
        MONGO_DB_PWD = password
    ```
    
    Env is used as an alternative for defining environment variables in Docker Compose. It is better to define the environment variable in docker-compose as it will be easier to make changes to it, in case something got changed or updated instead of rebuilding the whole image again.
    
2. **RUN**
    
    ```bash
    RUN mkdir -p/home/app
    ```
    
    RUN can run any kind of Linux terminal command. Here in this command, a new directory is assigned to be built using **mkdir** command which will be stored or created inside the Docker environment and not in the localhost or in the laptop memory we would be programming at the moment.
    
3. **COPY**
    
    ```bash
    COPY ./home/app
    ```
    
    Unlike RUN instruction where RUN cp will execute within my container not in my localhost, COPY will be functioning within the localhost as this command is used for copying the file or data present in the localhost or the laptop's memory into the container where it will be copied.
    
4. **CMD**
    
    ```bash
    CMD ["node", "server.js"]
    ```
    
    CMD is the entry-level Linux command by which we would be able to run/start the image we installed in the FROM instruction earlier as node.
    
    Here in \["node", "server.js"\] is represented as node server.js.
    
    We are able to do it because the node image was pre-installed onto the system.
    

The listed Dockerfile Instruction will be written in the code editor like VS Code like:-

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686809583882/26c4147c-e23c-4658-8834-bbb661f36369.png align="center")

So in the Dockerfile, we can also mention some version of the base image we are using in the example we have been using node:13-alpine but for example, let's take the latest 20-alpine3.17, then we can mention it in the same way.

If we want to view the new version available it can be viewed from the DockerHub and then going to the versions available of the selected image which we would be taking as the base image.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686810248998/095f0c38-57d8-453c-8177-9b3d44c20624.png align="center")

Now when we click on the selected image version we would be able to see the image container of that version as well.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686810393756/867e742e-35d1-4e7a-82f1-285523273d6e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686810403728/815896a8-83b2-4098-8c28-ce1793dbc439.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686810425767/e7090f7e-48c8-4309-8b24-b488ab7b6d80.png align="center")

Now as told earlier that every image is built on a base image, we can see that step to be followed here as well where version 20-alpine3.17 is based on the version node alpine3.17 and then all other things are followed in the same manner as discussed earlier in the Dockerfile instructions section.

**After creating the Dockerfile save the file with the exact name of the Dockerfile ( with 'D' in the capital at the start of the name.)**

# Building Image out of Dockerfile

To Build an image out of Dockerfile:-

1. Open up a terminal.
    
2. Locate the path of the file where we want to save this image on the system.
    
3. Give our Image a name in the terminal by:-
    
    ```bash
    docker build -t <Image_name> <Path-to-Dcokerfile>
    ```
    
    &lt;Path-to-Dockerfile&gt; is the path to the Dockerfile which we told Docker to use. If the Dockerfile is present in the same directory in which the Docker Image will be saved then the code with a "."(in the end) represent the current directory.
    
    ```bash
    docker build -t <Image_name> .
    ```
    
    The `docker build` command takes the path to the *build context* as an argument. The build context defines which paths you can reference within your Dockerfile. Paths outside the build context will be invisible to Dockerfile instructions such as `COPY`. It’s most common to set the build context to `.`, as in this example, to refer to your working directory.
    
    Ok so in various conditions the path we provided to the command line may contain multiple Dcokerfile which might create errors so to end up this problem we could use:-
    
    ```bash
    $ docker build -f dockerfiles/app.dockerfile -t demo-image:latest .
    ```
    
    where **\-f** is also a command used to point out the path of the dockerfile but it turns out to be more precise and tells out the "dockerfiles" present in the current directory inside which is the app.dockerfile inside which our file demo-image:latest is present which is named by the **\-t** tag.
    
4. Finally, when our image is generated we can view it by writing:--
    
    ```bash
    docker images
    ```
    
    and to get the list of all the containers in the command line running in our container:--
    
    ```bash
    docker ps
    ```
    

## Precautions and Methods to Solve Errors

1. Whenever you adjust Dockerfile You Must rebuild the Image!!
    
    It is recommended to rebuild the image whenever you change or adjust your Dockerfile otherwise, it may result in some errors.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686815071288/4e689bcb-a405-4280-9690-77263629433a.png align="center")
    
2. When you are done adjusting the Dockerfile and finally saved your adjusted file, then you may wish to delete the Docker image you created but, before deleting the Docker Image you may require to delete the Docker Image container first by the following commands:--
    
    ```bash
    docker ps -a | grep <Image-ID>
    ```
    
    then delete the Docker image container:--
    
    ```bash
    docker rm <conatiner-ID>
    ```
    
    Then we can finally delete the Docker Images:--
    
    ```bash
    docker rmi <image-ID>
    ```
    
3. Sometimes it is possible that in some containers the bash isn't installed so we can try running shell instead in that condition:--
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686816214778/f17c9b97-b8db-4a03-a29b-c921f8742a4a.png align="center")
    
    Also when we enter into the container by specifying its Container\_ID in the command:--
    
    ```bash
    docker exc <Conatiner_ID> /bin/bash
    ```
    
    We would be able to get access to the binary files of the container and if we try entering the environment of the container we will see the environment we referred to in the starting available in the environment of the container.
    
4. Sometimes, the latest versions may bring certain changes which may result in causing errors to our code so instead, specify a certain specific version of the image like node:16(for example) which we will be using as a base image while creating a dockerfile.
    
5. Use safer and trusted base images only in order to save your containers from malware and any security issues.
    
6. Use HEALTHCHECK to check container health by enabling HEALTHCHECK instructions to your Dockerfile.
    
    ```bash
    HEALTHCHECK --timeout=3s CMD curl -f http://localhost || exit
    ```
    
    Orchestrators like Kubernetes Docker Swarm can use this information to automatically restart problematic containers. The HEALTH of your containers is displayed when you run --&gt; docker ps command
    
    ```bash
    $ docker ps
    CONTAINER ID   IMAGE                	COMMAND              CREATED    	STATUS
    335889ed4698   demo-image:latest      "httpd-foreground"   2 hours ago	Up 2 hours (healthy)
    ```
    
7. Don't use important secretes in your images like passwords and API keys as these if these images reach into the hands of anyone else which can create harm to your system and architecture then things might get pretty ugly and get out of hand quickly.
    
8. Managing your Images by connecting arbitrary metadata with them by using Dockerfile LABEL to specify them with more relevant data possible and make the process more easy and fast while working in a team.
    
    ```bash
    LABEL com.example.project=api
    LABEL com.example.team=backend
    ```
    
9. Images can spread up to acquiring huge chunks of storage so to resist any slowing down of speed and efficiency try to keep your images small in size.
    
10. Docker defaults to running container processes as root. This is problematic because the root in the container is the same as the root on your host. A malicious process that escapes the container’s isolation could run arbitrary commands on your Docker host.
    
    You can mitigate this risk by including the USER instruction in your Dockerfile. This sets the user and group on which your container will run as. It’s good practice to assign a non-root user in all of your Dockerfiles:
    
    ```bash
    # set the user
    USER demo-app
    
    # set the user with a UID
    USER 1000
    
    # set the user and group
    USER demo-app:demo-group
    ```
    

# What happens next??

After we are done with creating Dockerfile, Jenkins comes into use which takes Dockerfile along with the code and creates an image based on the instructions provided in the Dockerfile.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686819075839/244ad173-6fad-498e-a697-ffe7c8658780.png align="center")

Usually, we work with a team on these projects and thus in order to make that file available for everyone the image is then pushed to Docker Repository so that people can download it and make changes locally or else it is deployed to a development Server so that whole team can get access to the file.

Thanks for reading my blog hope, I keep up the sharing in public motto and share my learnings 😄😄.

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile: [Aryan\_2407](https://twitter.com/Aryan_2407)

Anyway, if you want any more knowledge about Docker or Devops and how things work, keep an eye on my blogging channel or visit

[https://spacelift.io/blog](https://spacelift.io/blog)