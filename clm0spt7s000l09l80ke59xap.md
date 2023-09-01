---
title: "Linux Foundation Certificate- Training 01"
seoTitle: "Linux Foundation Certificate- Training 01"
seoDescription: "In this blog, I will be starting with the basics of Linux Terminal Command-line required for passing the Linux Foundation Certified Sys Administrator Exam."
datePublished: Fri Sep 01 2023 16:14:50 GMT+0000 (Coordinated Universal Time)
cuid: clm0spt7s000l09l80ke59xap
slug: linux-foundation-certificate-training-01
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693585220527/e12f40e9-f2b9-4213-b018-45883b262c84.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1693585248215/c3369ac6-a2d7-4820-9a24-1e11524d8fd5.jpeg
tags: linux, system-architecture, hashnode, linux-basics, wemakedevs

---

# Linux Foundation Certified System Administrator(LFCSA)

The Linux Foundation Certified System Administrator (LFCSA) is a certification program offered by the Linux Foundation. It's designed for individuals who want to demonstrate their skills and knowledge in Linux system administration. This certification is valuable for anyone pursuing a career in Linux administration or working with Linux-based systems.

Here are some key details about the LFCSA certification:

1. **Skills Assessed:** The LFCSA certification tests your abilities in several areas, including system architecture, file and directory management, system maintenance, networking, and security.
    
2. **Linux Distributions:** The certification is distribution-agnostic, which means it doesn't focus on a specific Linux distribution. Instead, it covers Linux concepts and commands that are applicable across various distributions, such as Ubuntu, CentOS, and Red Hat.
    
3. **Exam Format:** To earn the LFCSA certification, you need to pass an exam. The exam is a hands-on performance-based test where you are given real-world scenarios to solve using Linux commands and utilities. You must demonstrate your practical skills in system administration.
    
4. **Preparation:** To prepare for the LFCSA exam, it's essential to have a strong understanding of Linux fundamentals, as well as practical experience in administering Linux systems. You can also find study materials, online courses, and practice exams provided by the Linux Foundation to help you prepare.
    
5. **Career Benefits:** Achieving the LFCSA certification can boost your career prospects in Linux system administration and related fields. It's recognized by many employers as a validation of your skills and can help you stand out in the job market.
    
6. **Linux Foundation:** The Linux Foundation is a respected organization in the open-source community, and its certifications are well-regarded within the industry. Earning an LFCSA certification can be a valuable step in your career advancement.
    

# Training-01

SSH Daemon listens for any incoming connection. To convert to this remote daemon we will need **ssh** client program.

```bash
ip a
```

To get the IP address of your system.

```bash
ssh username@ip_address
```

To start using ssh in your system with the specified IP Address.

In case, if it gives any error while giving the command for using ssh with the ip address provided in the code.

```bash
sudo apt install ssh
```

If still, after installing the ssh on the system, it gives an error then we may see all the installed packages on the system as

```bash
sudo apt list --install
```

By this, you can view all the installed packages on the system which could be quite messed up, so organize and filter your data, we could use the command

```bash
sudo apt list --install/ grep openssh-server
```

Or, else just view the status of the installed package whether it is running or not as:-

```bash
sudo servcie ssh server
```

If the package is running then it should be noted as working in the result of this command but if not then, we may start the package by:

```bash
sudo service ssh start
```

This should be running in the Linux environment but if we are using it in Windows then we may write:

```bash
sudo systemctl ssh start
```

"apropos" is a help command that returns all the commands related to the director:

```bash
apropos director
```

But, it gives an error in starting as we have been in any database so:

```bash
sudo mandb
```

## Helping-Commands

There are various helping commands as well we use in the terminal command line in order to get info about various commands in the required format we want to attain such as :

```bash
ls --help
```

`help` is a built-in command in many shell environments like Bash. It provides brief help information for shell built-in commands like ls in this case and some shell functions.

Typically, it provides basic usage information and lists available options for built-in commands and is often used for getting quick information about shell-specific commands or functions.

```bash
man ls
```

`man` is a command that provides detailed documentation, or "manual pages," for a wide range of commands and utilities installed on your system and is not limited to shell built-ins; it covers both system and user-installed commands.

It offers comprehensive information, including detailed descriptions of a command's functionality, usage, options, and examples. It's the go-to tool for getting in-depth information about any command on your system.

```bash
apropos
```

which was mentioned earlier in the previous example for getting information about the command being mentioned.

## Command-completion method

In case we want to view the number of different commands that could be combined with any particular command of our own choice we may put down a space after the command and then press "Tab" twice in the function to list all the possible commands-combinations as:-

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693574688284/6b0b0dc5-9a16-446e-a167-3abd18bc4faa.png align="center")

Here as mentioned in the command, as soon as we write systemctl and then a space followed by pressing "Tab" twice we get to know the various command combinations that could be used with the systemctl command.

* It could also be used as the command-completion method as well like for example we wrote:
    

```bash
systemctl list-dep
```

Then if we press "Tab" twice quickly after writing dep in the command we will get our code completed as `systemctl list-dependencies` if the list-dependencies file is available to be used with systemctl.

* We can also use this Tab pressing command to list down the contents of the directory being listed in the terminal command line. For example, if we had written `/usr/` and then pressed Tab twice would list down the contents inside the directory without getting to enter into the directory by using `ls` command.
    

## Listing-Commands

```bash
ls -a
```

Here by this command, the hidden files will be visible present in the directory/ folder.

```bash
ls -l /var/log
```

Here it will list all the details of the directory in long form with separate columns listing all the permissions to be reviewed & overwritten for all different items and files in the directory, user name, name of group and when was it last updated.

```bash
ls -alh
```

Here it will list all the files hidden files as well same as `ls -a` along with some human-readable format defined as well like in the form of Kb, mb, Gb, etc.

# FileSystem Tree

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693582187419/d04d3c40-6313-4f1d-94ee-8a829ca85aa0.jpeg align="center")

It is considered a "Tree" in the downward form as here root is at the top and leaves & branches go downwards.

The path is also written in the same way from up to down to the directory/ file like `/home/jason/Documents/Invoice.pdf` (if Invoice.pdf is present in the Documents directory of jason family).

Now there are certain commands used to give certain required results as:

1. ```bash
     pwd
    ```
    

"pwd" stands for Print working directory which will print the current directory we are working/ operating in, along with the path specified with it, like `/home/jason/Documents`.

1. ```bash
     cd/
    ```
    
    will move us to the root directory.
    
2. ```bash
     cd -
    ```
    
    Go to the previous directory.
    
3. ```bash
     cd
    ```
    
    Go to the home directory.
    
4. ```bash
     cp [source][destination]
    ```
    
    Here it is the format for copying the file from the source location to the destination.
    
5. ```bash
     cp -r [source][destination]
    ```
    
    "r" stands for the recurser in the code which helps in copying the whole content from the source to the destination folder/ directory(copying everything in it).
    
6. ```bash
     mv [source][destination]
    ```
    
    It is similar to the cut option in Windows used for Linux.
    
7. ```bash
     rm file_name
    ```
    
    To delete a file.
    
8. ```bash
     rm -r Invoices/
    ```
    
    Delete all the files, folders and sub-directories from the directory.
    
9. ```bash
     echo "Pic(1) was created" > Pictures/family.jpg
    ```
    
    The picture is created family\_dog.jpg with the tag "Pic(1) was created".
    

Hope you get to learn some from this blog for which you came here 😄. Soon I will be releasing other blogs explaining **Inode features, Hard Links, Soft Links, bits and purposes** in the system and various other commands for system management and organizing.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693584082290/c901eaf2-ad2f-4ea7-b794-e53bc15a8929.gif align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[Aryan\_2407](https://twitter.com/Aryan_2407)