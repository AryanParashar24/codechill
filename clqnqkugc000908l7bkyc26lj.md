---
title: "Infrastructure as Code(Iac): Terraform vs Pulumi who's the Winner?👑"
seoTitle: "Infrastructure as Code(Iac): Terraform vs Pulumi who's the Winner?👑"
seoDescription: "Here in this blog we will not only, get to know about the features & services behind excitement have bubbled up in the minds of every developer & Investor"
datePublished: Wed Dec 27 2023 12:12:31 GMT+0000 (Coordinated Universal Time)
cuid: clqnqkugc000908l7bkyc26lj
slug: infrastructure-as-codeiac-terraform-vs-pulumi-whos-the-winner
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703678802269/7ab9c631-13e8-412d-b471-e875273a9963.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1703679052444/d80f137f-94a8-42cf-9c0a-f726a23ecb06.jpeg
tags: cloud, software-development, kubernetes, cloud-computing, devops, infrastructure, terraform

---

Here in this blog we will not only, get to know about the features and services based on which a state of excitement have bubbled up in the minds of every developer, team lead or investors but will also clear what is Infrastructure as Code(Ias) in case anyone wants to learn about it from starting or left on its goals. If you wants to jump to the difference part than follow the table of content and jump on to your favourable topic.

Terraform has been the prominent leader in the Infrastructure as Code even after having a so many alternatives like Pulumi, AWS CloudFormation, Ansible, Chef, Packer & Cloudify, but as the time pass-by we are witnessing the thriving services of Pulumi becoming the major topic of discussion amongst the developers and investors for managing their infrastructure. Before getting to know about the game changing features provided by so many tools, we need to know about the Infrastructure as Code and it's requirement.

Since terraform is the dominating service in the Infrastructure as Code, thus it's really important to know about the services being provided by Terraform and then trace out the difference between the Pulumi and Terraform, based on these features and approaches adopted by them to developers and their teams we can reach out to the required answer according to our requirements of roles.

# History of Development Process

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703529969077/58333bd8-4a92-43be-bd46-cf84c98e990d.png align="center")

Earlier for a development process, there were a lot more processes involved and capital invested from the human, time and hardware point of view as:

1. Firstly, businessmen and companies pitch a requirement for apps.
    
2. Business analyst oversee the requirements and converts them into the high level tech requirement.
    
3. Then the Solution Analyst/ Technical lead will convert the design/ idea and build a technical infrastructure including specs, frameworks and servers needed. Design frontend and backend for the application, thus everyone planned will be onto the premise.
    
4. Any requests related to hardware purchase or premise request will be told to procurement team with vendors and can even take days, weeks, months to reach data center.
    
5. Once it reaches the data center, field engineers will take care of equipment.
    
6. System Administrators will make initial configurations and the network administrators who make network available.
    
7. Storage Admins assigns storage to system and backup engineers provides backups.
    
8. Once the systems are sealed, they can be forwarded to application teams to deploy their application.
    
9. Once we settled them up, to maintain we were required to update versions, deploy new version release, DB backups/ updates, recover apps and add/ recover servers.
    

All of these development processes decrease the efficiency drastically and slow down development process, expensive, limits Automation and have very slow scalability possibility.

It is highly Inconsistent and servers are sized depending on peak utilization so waste a lot of resources. Unavailability to scale up or down supply means these resources won't be used during off-peak hours.

## Modern Solution

Thus, most of the organizations have moved to the virtualization of these resources to limit these disadvantages and work efficiently such as Microsoft Azure, Amazon AWS, Google cloud platform, with cloud we don't have to worry about most of the things like database center, hardware assets and storage aren't required to look into if we are on cloud as all of these taken care by cloud providers.

Virtual machines can be spun up in the minutes saving up a lot of days, weeks, months compared to earlier and time to market reduced from months to weeks or even days in cloud environment. Human requirements are also reduced saving up money, cloud provides a way to use APIs, which opens a whole new world of security and finally, the build in Auto Scaling and elastic functionality of cloud infrastructure reduces resources wastage.

With virtualization and cloud we can now provide infrastructure within few clicks which considerably saves up a lot of time and efforts from traditional methods, still having management console for resource provisioning is not always the ideal solution.

It's okay to adopt it's use in small organizations but on large scale resources, elastic and highly scalable cloud environment with immutable infrastructure isn't considered feasable. Once provisioned, a lot teams still have to work for a lot of overhead processes which will eventually increase delivery time and chances of human errors are still large resulting in inconsistent environment.

Everyone came up with different tools and services to provide all of these functionalities of automating infrastructure provisioning to deploy faster and in a consistent fashion cloud environment for which people chosen different tools some chosen basic tools like Shell script while many others chosen programming languages like Python, Perl, Ruby and Powershell.

These problems were being solved by the sector including programming and code to solve the application infrastructure problem and this came to known as the Infrastructure as Code(Ias) including tools like Docker, Ansible, Terraform, CloudFoundation, Packer, Puppet, Vagrant and SaltStack.

# Infrastructure as Code Introduction

Infrastructure as Code helps in automating all of these tasks without getting to set up huge operation and admin teams. Some programs and applications programmed to perform all of these tasks, amongst which we have so many tools for handling different functionalities.

## Services & Functionalities:

1. ### Infrastructure provisioning
    
    It manages out the following tasks:
    

* Spinning up the new servers
    
* Network Configurations
    
* Creating load balancers
    
* configuring on infrastructural level
    
    **<mark>Traditional Approach</mark>:** In traditional setups, provisioning infrastructure involved manual tasks like setting up servers, configuring networks, and installing software.
    
    **<mark>IaC Approach</mark>:** With IaC, you define your infrastructure requirements in a declarative or imperative script. This script can be version-controlled and executed to automatically provision the required infrastructure.
    

1. ### Configuration of provisioned infrastructure
    
    It manages the following tasks:
    

* Installing application on server
    
* Managing those applications
    
* prepare infrastructure to deploy your applications
    
    **<mark>Traditional Approach</mark>:** Configuring infrastructure settings manually can lead to inconsistencies and errors.
    
    **<mark>IaC Approach</mark>:** IaC not only provisions infrastructure but also configures it. You can define the desired state of your infrastructure in code, ensuring consistency across different environments. Tools like Ansible, Chef, or Puppet can help with configuration management.
    

1. ### Deployment of Application
    

With Docker containers configuration and deployment step combined, involving configuration of our application and then packaging it with similar environment according to it's needs.

So, if we have our application configured in packages and then if you provision infrastructure and install Docker runtime, we don't need to configure much of our servers and install much servers by just using one docker container.

**<mark>Traditional Approach</mark>:** Deploying applications manually can be time-consuming and error-prone.

**<mark>IaC Approach</mark>:** IaC extends to application deployment. You can define how your applications should be deployed, including dependencies and configurations. Continuous Integration/Continuous Deployment (CI/CD) pipelines can automate the deployment process, ensuring that code changes are consistently and reliably deployed.

## Attributes Characteristics

### **1\. Phases: Initial vs. Maintainer:**

* **Initial Phase:**
    
    * Involves setting up the initial infrastructure and applications.
        
    * Different tools may have varying emphasis on initial setup vs. ongoing maintenance.
        
* **Maintainer Phase:**
    
    * Focuses on ongoing management, updates, and scaling of infrastructure and applications.
        
    * Tools may prioritize ongoing maintenance tasks over initial setup.
        

### **2\. Declarative vs. Procedural Approach:**

* **Declarative Approach:**
    
    * Describes the desired state without specifying how to achieve it.
        
    * Configuration files or code express the intended outcome rather than the steps to reach it.
        
* **Procedural Approach:**
    
    * Specifies step-by-step instructions to achieve a result.
        
    * Emphasizes a sequence of actions to reach the desired state.
        

### **3\. Mutable vs. Immutable Infrastructure:**

* **Mutable Infrastructure:**
    
    * Involves making changes to existing infrastructure.
        
    * Updates are applied to the current state of infrastructure.
        
* **Immutable Infrastructure:**
    
    * Requires replacing existing infrastructure with a new version.
        
    * Infrastructure is treated as disposable, and changes are implemented by creating new instances.
        

### **4\. Agent vs. Agentless:**

* **Agent-Based (With Agent):**
    
    * Requires installing an agent on managed nodes.
        
    * Agents facilitate communication and execution of tasks on the managed infrastructure.
        
* **Agentless (Without Agent):**
    
    * Operates without a separate agent on managed nodes.
        
    * Communication and task execution are achieved without the need for dedicated agents.
        

### **5\. Master vs. Masterless:**

* **Master/Server-Client Model (With Master):**
    
    * Involves a centralized server or master that controls configuration distribution.
        
    * Configuration changes are managed and distributed from a central authority.
        
* **Masterless (Without Master):**
    
    * Operates without a central server; configuration is distributed without a master.
        
    * Configuration changes are applied directly to individual nodes without central orchestration.
        

# Terraform

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703674026004/2da8a1ab-012c-4f8d-9b9c-80817741f3d4.jpeg align="center")

Terraform is a popular Infrastructure as Code, which is specifically useful as an infrastructure provisioning tool. It is an Open Source tool which is developed by Hashicorp, which installs as a simple binary that can be settled up quickly allowing us to build manage and destroy infrastructures in a matter of minutes. One of the advantage of Terraform is it's ability to deploy infrastructure across multiple platforms including to deploy infrastructure across multiple platform including public and private cloud such as on-premise, vsphere cluster or cloud solution such as AWS GCP, Azure and many more.

### Managing to Multiple Platform

Providers helps terraform manage onto so many different platform and manage third party platform through their API providers which helps Terraform manage cloud platforms like AWS GCP or Azure and other infrastructure like big-ip, cloudfare, DNS, Palo Alto, infoblox. For monitoring and data management tools like Datalog, Grafana, Auth0, Wavefront and Sumo logic.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703645397674/a11b7205-ca23-4145-988b-a53d8ebce549.png align="center")

For handling Databases, tools like Influx DB, MongoDB, MySQL, Postgres SQL, VCS (Version control systems) like GitHub, GitLab and BigBucket.

Terraform supports hundreds of such providers and as a result, we can work with almost every infrastructure platform. Terraform uses HCL (Hashicorp configuration language) which is a simple declarative language to be provisioned as a block of code where all infrastructure can be defined within configuration file which has a `.tf` file extension. The configuration syntex is easy to read and write, with easily understandable and beginner-friendly nature, which is used to provision a new ec2 instance on AWS cloud.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703646512458/9b2c9589-28e1-481a-9151-ebf8037fc733.png align="center")

Due to its declarative nature it can be used/ maintained in a version control system allowing it to be declarative to other teams. Declarative means that the code has been pre-defined according to our desired state for infrastructure.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703646827029/7cc3793f-520c-4b88-a8c2-51a7ca12a712.png align="center")

Here at the right initially, there will be nothing present as the infrastructure but it will son be taken care by the Terraform to go from the current state to the required desired state without us having to worry about, how to reach the required state or ideal infrastructure.

### Phases

Terraform works in three phases: `init`**,** `plan` **and** `apply`.

During `init` phase terraform initializes the project and identifies the providers to be used for target environment.

During the `terraform plan` phase is the step in Terraform where it generates an execution plan. This plan outlines what changes Terraform will apply to your infrastructure to reach the desired state specified in your Terraform configuration files.

During the `apply` phase, terraform makes the necessary changes required on target environment to bring it to desired state. If for some reasons, environment wants to shift to desired state then a subsequent terraform apply will bring it back to desired state only by fixing the missing component.

### Resources

Every object terraform manages is called a Resource, a resource can be complete instance of a database server in cloud or in a physical server on-premise managed by Terraform.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703649531894/9cf8db68-6343-447e-86b7-882b7e473f34.png align="center")

Terraform manages the life cycle of resource from its provisioning, configuration to decommissioning to record the state of infrastructure based on real world based and based on this it can determine what actions you take while updating resources for a particular platform Terraform can also ensure that the entire infrastructure is always in the defined state at all times, the state is a blueprint of infrastructure deployed by Terraform.

Terraform can read attributes of the existing infrastructure components by configuring data sources which can later be used for configuring other resources. It can even import other resources from outside the Terraform that were either created manually or by means of other IEC tools and bring it under its control so that it can manage those resources going forward.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703649664932/2c9370cd-a522-4e9d-8e9e-c2a9e6124687.png align="center")

Terraform cloud and Terraform Enterprise provide additional features that allow simplified collaboration between teams, managing infrastructure improved security and a centralized UI to manage Terraform deployments, all of these features perform an excellent enterprise grade infrastructure provisioning tool.

### Downloading Terraform

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703650071473/a0dcd75e-4f11-4627-8edc-b7895a0bcef0.png align="center")

Terraform can be downloaded as a single binary or executable file from the terraform download section as a simple downloading, and copying it to the system path whose version we can check once installed.

Terraform uses configuration files which are written in HCL to deploy infrastructural resources, these files have `.tf` extension and can be created by any text editor even notepad or windows command line text editor, vim or emac in Linux or any other ide like VS Code or many more.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703651610962/542a0106-4888-4a7c-9726-dcdab9130ed9.png align="center")

A resource in Terraform is an entity managed by Terraform, representing various elements such as files on a local host, virtual machines in the cloud (e.g., EC2 instances), or services like S3 buckets, ECS, DynamoDB tables, IAM users, IAM groups, roles, policies, and more. Essentially, a resource encapsulates the configuration and attributes of a specific component within your infrastructure that Terraform is responsible for managing or it could be resources on major cloud providers such as compute and app engine from GCP, databases like Azure, Azure active directory, etc. There are hundreds of resources that can be provisioned across most of the cloud and on-premise infrastructure using terraform.

## Using Terraform config files and Providers

<mark>terraform init :</mark>

When we run it in a directory containing the config files, terraform downloads and installs plugins for the providers used within the configuration. These can be plugins for cloud providers such as AWS, GCP, Azure or something as simple as local providers which can be used to create a local file type resource.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703657232532/abb1fb45-e915-4097-a629-ce0bf36808b2.png align="center")

Terraform uses plugin based architecture to work with hundreds of such infrastructure platforms. Terraform providers are distributed by Hashicorp and are publicly available in terraform registry at [registry.terraform](https://registry.terraform.io/) that contains three tiers of providers:

<mark>First tier</mark> are the official providers that are runned and maintained by Hashicorp and include major cloud providers such as AWS, GCP and Azure, also the local providers we use comes under the official providers.

<mark>Second tier</mark> are verified providers which are owned and maintained by a third party technology company that has gone through a partner provider process with Hashicorp like big-ip provider from F5Network, Heroku and DigitalOcea.

<mark>Third tier</mark> are the community providers that are published and maintained by individual contributors of Hashicorp community.

The `terraform init` command shows the version of plugin installed onto the system or network. As in the picture we can see, that we are using the Hashicorp verison 2.0.0, terraform init is a safe command and can run as many times as required without impacting the actual infrastructure being deployed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703661913438/a797e180-ca15-4860-a66a-b0e1a4a3f7c8.png align="center")

The plugins are downloaded into a hidden directory called .terraform/plugin\_name in the working directory containing configuration files. The plugin name is hashicorp/local, also known as source address which is an identifier used by terraform to locate and download plugin from registry.

The first part of the name which is this case is hashicorp, which is the organizational namespace, followed by type which is the name of provider such as local. The plugin name as also optionally have a host name in front, which is the name of the registry where plugin is located, if omitted it will default to registery.terraform.io which is hashicorp public registry given the fact that local provider is stored in public terraform registry within the hashicorp namespace.

source address: registry.terraform.io/hashicorp/local

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703671865408/7b147d71-e353-4c6e-b871-73bd19dae111.png align="center")

<mark>terraform validate</mark> :

Once we write our config files it's not necessary to run `terraform plan` or `terraform apply` to check if syntex used is correct, instead we can make use of `terraform validate` command and if everything is correct with the file, we should see a successful message otherwise in case of any error we will see the `validate` command showing us the line causing problem in the configuration file and will also suggest solutions to fix it.

<mark>terraform fmt</mark> :

This is the terraform format command whic hscans the configuration file in the current working directory and formats the code in canonical format which is a useful command to improve the readability of terraform config file. When we run this command, the files that are changed in config file are displayed on the screen.

<mark>terraform show</mark> :

This command will print out the current state of the infrastructure as seen by terraform. After we have already created the local file resources, on running terraform show command we will be shown the current state of the resources including all the attributes created by terraform.

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703671969633/4fed5e82-600c-43ba-9a72-6f70b75b3447.png align="center")

<mark>terraform providers</mark> :

This will show a list of all the providers used int the configuration directory. We can even use `terraform provider mirror` to copy provider the plugin needed for the current configuration to another directory like this command will mirror the provider configuration in a new path.

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703671992054/a2ec7461-502d-4b75-9c64-a437f785a39c.png align="center")

<mark>terraform output</mark> :

This will print all output variable in the configuration directory. You can also print the value of a specific variable by appending the name of variable to the end of the output.

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703672019288/2e0b79ca-5c45-4250-95cf-c51ee953ddf5.png align="center")

<mark>terraform refresh</mark> :

This command sync terraform with real world infrastructure. If there are any changes made to a resource created by terraform outside it's control such as a manual update it's created, such as manually updating the terraform state file, this reconciliation is useful to determine what action take during the next apply which will not only modify any infrastructure resource but it will also modify the state of the file.

Terraform refresh run automatically by commands such as terraform plan and terraform apply and this is done prior to terraform generating an execution plan, it can be by-passed as well by using the dash refresh equal to false option with commands.

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703672046663/d96c4eca-69a2-4f79-a249-8e696b158b37.png align="center")

<mark>terraform graph</mark> :

This command is used to create a visual representation of dependencies in a terraform configuration or an execution plan. Upon running the `teraform graph` command we will have an output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703672084068/efda8adf-a74d-48dc-a6ff-d465c906dc22.png align="center")

The text generated is hard to comprehense as it's graph generated in a format called dot to make more sense of this graph, we can pass it through a graph visualization software such as graph viz and we can install it in Ubuntu, once installed we can pass the output of `terraform graph` to dot command which we installed using graph face package and generate graphic which we can open now using browser and it should show a dependency graph.

---

# Pulumi

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703674111759/6068ea08-3d10-4978-bb73-2071049693b5.jpeg align="center")

Pulumi is an open source Infrastructure as Code platform that helps teams tame the cloud’s complexity using the world’s most popular programming languages (TypeScript, Go, .NET, Python, and Java) and markup languages (YAML, CUE).

## Features:

1. **Languages Adaptability :**
    

This innovative approach allows software engineers and platform engineering teams to manage complex cloud architectures and internal developer platforms more efficiently and effectively. If you are new to Infrastructure as Code and have prior knowledge over languages like Python, Typescript, JavaScript, Go, Java or YAML, you can make best use of these skills in Iac through Pulumi unlike Terraform where we need to use HCL (Hashicorp Configuration language as discussed above), traditional JSON or other domain-specific languages, thus simplifying and streamlining the process of provisioning and managing cloud infrastructure.

1. **Team Productivity & Compatibility:**
    

Developers within the team need not to rely on some domain specific languages to convert or managed before pushing their applciation to the production and they can continue to collaborate with each other in language they are most comfortable working, thus it will be much easier for them to take ownership of provisioning the necessary components and saving up capital and time.

1. **Testing:**
    

You can choose your favorite testing framework and develop unit and integration tests that perform the necessary validations on your infrastructure. For this time, I will be including a test been produced in the language Go:

```go
package main

import (
	"testing"

	"github.com/pulumi/pulumi/sdk/v3/go/auto"
	"github.com/stretchr/testify/assert"
)

func TestAWSS3BucketCreation(t *testing.T) {
	// Set up the environment for the Pulumi program
	stackName := "mystack"
	stack, err := auto.UpsertStackInlineSource(stackName, "mystack", pulumiProgram)
	if err != nil {
		t.Fatal(err)
	}

	// Execute the Pulumi program that creates the S3 bucket
	_, err = stack.Up(nil)
	if err != nil {
		t.Fatal(err)
	}

	// Verify that the S3 bucket was created successfully
	bucketName, err := stack.Output(bucketOutputName).Value()
	if err != nil {
		t.Fatal(err)
	}
	assert.NotNil(t, bucketName)
	assert.NotEmpty(t, bucketName)

	// Clean up
	_, err = stack.Destroy(nil)
	if err != nil {
		t.Fatal(err)
	}
}

// Pulumi program in Go
func pulumiProgram(ctx *auto.Context) error {
	bucket, err := s3.NewBucket(ctx, bucketName, nil)
	if err != nil {
		return err
	}

	ctx.Export(bucket.BucketName)

	return nil
}

// Constants
const (
	bucketOutputName = "bucketName"
	bucketName       = "mybucket"
)
```

1. **One Pipeline for Everyone:**
    
    ![](https://miro.medium.com/v2/resize:fit:875/1*5mJhC4ablu5UruxhdmE22Q.jpeg align="left")
    
    Pulumi lets you use one pipeline for Application code and Infrastructure code. Pulumi’s approach to infrastructure as code is great for continuous delivery because it uses source code to model cloud resources. This means updates to your cloud infrastructure can be reviewed, validated, and tested using the same process that you have today. For example, doing code reviews via Pull Requests, running code through linters or static analysis tools, and running unit and integration tests as appropriate. It all “just works” for your cloud infrastructure the same way it would for your application code.
    
    Pulumi can easily integrate into any continuous integration/continuous delivery (CI/CD) system.
    
2. **Pulumi has a secret storage:**
    
    It safeguards all sensitive data using integrated secret storage. This secret storage solution seamlessly functions across various deployment scenarios, whether you are using hosted Pulumi Service, the Self-Hosted Pulumi Service, or a self-managed backend. When you create a stack using ‘pulumi new’ or ‘pulumi stack init,’ the Pulumi Service automatically protects secrets. If you opt for a self-managed backend like AWS S3 or Google Cloud Storage, secrets are secured through a passphrase that you define when initiating a new stack with ‘pulumi new.’ Regardless of the scenario, each Pulumi stack receives a unique encryption key. Unlike Terraform which requires integration with a third-party solution to manage secrets.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703677689575/88b7fb50-0198-4d76-a699-18ef7b2ad60f.png align="center")
    
    For Terraform, state can also be stored remotely (with the use of proper backend config) and can be encrypted. By default however, it’s stored locally and is unencrypted - which could raise security concerns. For Terraform’s SaaS offering *Terraform Cloud*, both the traffic and the state are encrypted.
    
    It’s fair to say that both tools can be used securely, but Pulumi does provide a little more security out-of-the-box. Beyond that, it’s only a matter of setup and price for both SaaS offerings.
    
3. **Addressing Challenges in Cloud Infra. Management:**
    
    In the ever-evolving realm of cloud services, the intricacies of managing complex cloud architectures and developing internal platforms emerge as formidable challenges. Pulumi emerges as a powerful solution, offering a programmatic interface that empowers teams to seamlessly provision and control infrastructure. By bridging familiarity and efficiency, Pulumi becomes a vital tool in overcoming the complexities associated with modern cloud environments and internal platform development.
    
4. **Transforming Infrastructure Management:**
    
    As said in the previous points due to it's collaboration with general languages not only streamlines the learning curve for developers but also amplifies the flexibility and potency of infrastructure as code, setting it apart from the crowd and redefining the landscape of infrastructure management.
    
5. **One Pipeline for Everyone:**
    
    ![](https://miro.medium.com/v2/resize:fit:875/1*5mJhC4ablu5UruxhdmE22Q.jpeg align="left")
    
    Pulumi lets you use one pipeline for Application code and Infrastructure code. Pulumi’s approach to infrastructure as code is great for continuous delivery because it uses source code to model cloud resources. This means updates to your cloud infrastructure can be reviewed, validated, and tested using the same process that you have today. For example, doing code reviews via Pull Requests, running code through linters or static analysis tools, and running unit and integration tests as appropriate. It all “just works” for your cloud infrastructure the same way it would for your application code.
    
    Pulumi can easily integrate into any continuous integration/continuous delivery (CI/CD) system.
    
6. **Community Support and high Engagement:**
    
    Pulumi's ideal market consists of software engineers and platform engineering teams. These professionals benefit the most from Pulumi's approach, as they can leverage their existing coding skills to manage cloud resources more effectively. Getting involved with Pulumi's [**open source projects**](https://github.com/pulumi/pulumi), contributing to the development and enhancement of this groundbreaking platform can leverage our experience with Infrastructure as Code.
    
    For collaboration and expert support we can reach out to join Pulumi's [**Slack channel**](https://slack.pulumi.com/) to connect with other users and the Pulumi team for more insights.
    

Terraform has been dominating since a long time in the Infrastructure as Code and still going to manage it's popularity due to it's already existing huge circle of customers, but Pulumi is evolving as a warrior providing many new feature, opportunity to collaborate and more developer friendly which might brign up a lot of change within the definition of how people see Infrastructure as code these days and beleive me that day isn't very far from today.

Hope you get to find a lot of value out of this blog and might have gotten somewhat close to your choice in between both of these amazing tools of Cloud Native. Soon, I will be going to bring up a detailed blog specifically for Pulumi to help you out more into this journey, other than that if you are interesting in the DevOps and SRE tools collaboration in Artificial Intelligence then, I will soon going to release a blog on Kubiya.ai and some other cloud & system network security tools as well, becuase we have got a lot to discuss in K8s ☸️😄

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703678701494/9c2f5f70-63cb-4f29-997c-19762e08af42.gif align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)