---
title: "Why and How to Go Anonymous to Secure network🥷🥷"
seoTitle: "Why and How to Go Anonymous to Secure network🥷🥷"
seoDescription: "Why you should resist websites & companies to track your data and get to know about Tor Browser, VPN & a lot more anonyomous services"
datePublished: Wed Oct 11 2023 16:27:04 GMT+0000 (Coordinated Universal Time)
cuid: clnlyrm0k000309jw2tvygha6
slug: why-and-how-to-go-anonymous-to-secure-network
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697019066298/5de2c966-d99c-43ef-afa6-81562e00b063.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1697041476681/776169fa-7af7-4721-be6f-6860f1b14989.jpeg
tags: programming-blogs, technology, hacking, cybersecurity-1, wemakedevs

---

Every other website or platform we work or access services from, tracks us to get their services improved by getting user experience information or to make some money by selling ads to you based on your previous web activities on other platforms, which can vary from buying some product from amazon and then spamming ads to the user to our service providing platform with the products closely related to our search on those E-commerce platforms to the exams or the stream to which we belongs to giving them some accurate recommendations of the materials required to operate in that domain(e.g. performance mouse, gaming monitor or graphic cards to the professional gamers).

Even our emails are getting eavesdropped (read secretly) by Google, some professional Hackers or the National Security Agency(NSA) cataloging all our activities which finally specifies that our every online move is being watched or recorded.

# **The Social Dilemma: Digital Identity Risk**

There is a theory of what the big tech companies do with the data they collect from us and how could it be dangerous to us and humankind. So here the main question is:

### **Why do we need to secure our information and resist any information or data breach?**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697027028731/68bae19e-32e6-4720-b34d-0ae868f1b420.jpeg align="center")

One of the greatest movie being produced- The Social Dilemma, talks about how this information of all of us are being recorded, our every step, every action we do on the web whether it's upvoting, commenting, sharing, saving videos, posts, reels or any product. As Bruce Schneier the famous cryptographer and cyber security expert once said, "**<mark>If something is free, you're not the customer; you're the product</mark>**".

This information or the metadata acquired by these companies is often used to get you more acquired with their product and increase engagement for their product or their partner companies' products by providing you advertisements related to your interest or direct posts and content based on your previous activity.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697027961716/e031c19e-d3fa-41b5-a26d-3380e63307ff.jpeg align="center")

The main motive of these companies is to release as much dopamine as possible in your head and get you addicted to their applications, games or other products. To do it many professionals from the tech domain have said that these companies happen to form a real-life artificially intelligent model of your personality based on the content you consume, like, save or share with your friends and thus similarly similar content has been shared with you on the platform which could flood your mind with dopamine which is very dangerous as it creates a kind of illusion between the real world and the world in which you believe to exist which could harshly result in strikes, riots, effect election polls or can even put someone's life in danger.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697028418793/7a18f0f1-41ad-4a0f-9ef6-fd365e9cfeef.jpeg align="center")

It isn't like its not useful at all as it could reduce the time and bring some useful content or product for the customer which they have been looking for a long time without wasting any further time or can even bring a lot more help as well like for the charity works, marketing tasks for the events and hackathon which exactly happened earlier in the starting phase of all of these products but soon as it started growing, strangely it happen to start violating a lot of ethics and privacy.

# General Methods to Go Anonymous

To get rid of this tracking by these big firms or bodies we can adopt various methods, I will be getting you 4 general methods which will include navigating anonymously by:

* **The Onion Network (using Tor Browser)**
    
* **Virtual Private Networks (VPN)**
    
* **Proxy Servers**
    
* **Private encrypted email**
    

# How do we get Tracked anyway?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697041169300/f4321bde-3491-4bfd-b687-a82d6df17d5f.gif align="center")

First, before moving forward to how can we use the web anonymously we need to know how we get tracked by these big players in the tech domain or even by some other well-experienced hackers.

Your IP address identifies you as you traverse the internet. Data sent from your machine is generally tagged with your IP address, making your activities easy to track. Second, Google and other email services will “read” your email, looking for keywords to more efficiently serve your ads.

When you send a packet of data across the internet, it contains the IP addresses of the source and destination for the data. In this way, the packet knows where it is going and where to return the response. Each packet hops through multiple internet routers until it finds its destination and then hops back to the sender.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697040858323/81e21fd9-5cd7-46ec-b917-be256b36b3f0.gif align="center")

For general internet surfing, each hop is a router the packet passes through to get to its destination. There can be as many as 20–30 hops between the sender and the destination, but usually any packet will find its way to the destination in fewer than 15 hops. As the packet traverses the internet, anyone intercepting the packet can see who sent it, where it has been, and where it’s going.

This is one way websites can tell who you are when arrive and log you in automatically, and it’s also how someone can track where you’ve been on the internet.

To see what hops a packet might make between you and the destination, you can use the `traceroute` command in the command prompt or the terminal command line of your Linux OS version(like Kali, Ubuntu, etc). Simply enter traceroute and the destination IP address or domain, and the command will send out packets to the destination and trace the route of those packets.

```bash
traceout google.com
```

Your results will likely be different from others because your request would be coming from a different location and because Google has many servers across the globe. In addition, packets don’t always take the same route across the Becoming Secure and Anonymous 141 internet, so you might send another packet from your address to the same site and receive a different route.

# The Onion Router System

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697034975316/656ecdff-8d61-4884-bfd3-67c48b966972.jpeg align="center")

### History:

In the 1990s, the US Office of Naval Research (ONR) set out to develop a method for anonymously navigating the internet for espionage purposes. The plan was to set up a network of routers that was separate from the internet’s routers, that could encrypt the traffic, and that only stored the unencrypted IP address of the previous router—meaning all other router addresses along the way were encrypted. The idea was that anyone watching the traffic could not determine the origin or destination of the data. This research became known as “**<mark>The Onion Router (Tor) Project</mark>**” in 2002, and it’s now available to anyone to use for relatively safe and anonymous navigation on the web.

### How Tor Works

Packets sent over Tor are not sent over the regular routers so closely monitored by so many but rather are sent over a network of over 7,000 routers around the world, thanks to volunteers who allow their computers to be used by Tor. On top of using a separate router network, Tor encrypts the data, destination, and sender IP address of each packet. At each hop, the information is encrypted and then decrypted by the next hop when it’s received.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697034878951/a86f369d-5fb0-49c1-8b63-6a6db5cab9c7.png align="center")

In this way, each packet contains information about only the previous-hop along the path and not the IP address of the origin. If someone intercepts the traffic, they can see only the IP address of the previous hop, and the website owner can see only the IP address of the last router that sent the traffic. This ensures relative anonymity across the internet.

### DarkWeb on Tor

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697036661684/ce27616d-221c-4d99-92a4-b96d9d8403dd.jpeg align="center")

In addition to being capable of accessing nearly any website on the traditional internet, the Tor browser is capable of accessing the dark web. The websites that make up the dark web require anonymity, so they allow access only through the Tor browser, and they have addresses ending in .onion for their top-level domain (TLD). The dark web is infamous for illegal activity, but a number of legitimate services are also available there. A word of caution, however: when accessing the dark web, you may come across material that many will find offensive.

### Disadvantages of Tor

The tradeoff is that surfing via the Tor browser can be a lot slower; because there are not nearly as many routers, the bandwidth is limited in this network.

The intelligence and spy services of the United States and other nations consider the Tor network a threat to national security, believing such an anonymous network enables foreign governments and terrorists to communicate without being watched. As a result, several robust, ambitious research projects are working to break the anonymity of Tor.

### How Intelligence agencies like the NSA broke Tor

Tor’s anonymity has been broken before by these authorities and will likely be broken again. The NSA, as one instance, runs its own Tor routers, meaning that your traffic may be traversing the NSA’s routers when you use Becoming Secure and Anonymous 143 Tor. If your traffic is exiting the NSA’s routers, that’s even worse, because the exit router always knows your destination. The NSA also has a method known as traffic correlation, which involves looking for patterns in incoming and outgoing traffic, that has been able to break Tor’s anonymity.

Though these attempts to break Tor won’t affect Tor’s effectiveness at obscuring your identity from commercial services, such as Google, they may limit the browser’s effectiveness in keeping you anonymous from spy agencies.

# Virtual Private Networks (VPN)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697039045109/f78efff8-257d-48cd-adaa-0efd75fb3ed6.png align="center")

Using a virtual private network (VPN) can be an effective way to keep your web traffic relatively anonymous and secure. A VPN is used to connect to an intermediary internet device such as a router that sends your traffic to its ultimate destination tagged with the IP address of the router.

### Mechanism

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697039118640/26348a59-c95b-406c-a344-fe4d7ca81eb2.png align="center")

The beauty of VPNs is that they are simple and easy to work with. You can open an account with a VPN provider and then seamlessly connect to the VPN each time you log on to your computer. You would use your browser as usual to navigate the web, but it will appear to anyone watching that your traffic is coming from the IP address and location of the internet VPN device and not your own. In addition, all traffic between you and the VPN device is encrypted, so even your internet service provider can’t see your traffic.

### Advantages

Among other things, a VPN can be effective in evading government-controlled content and information censors. For instance, if your national government limits your access to websites with a particular political message, you can likely use a VPN based outside your country to access that content.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697039184726/622e1056-8769-4518-8333-2ff442d20e50.jpeg align="center")

The strength of a VPN is that all your traffic is encrypted when it leaves your computer, thus protecting you against snooping, and your IP address is cloaked by the VPN IP address when you visit a site.

Here are some of the famous secured VPNs:

* NordVPN
    
* ExpressVPN
    
* CyberGhost
    
* Private Internet Access
    
* Hide My Ass (HMA) ***LOL !!***
    
* PureVPN
    

### Disadvantages

Using a VPN can certainly enhance your security and privacy, but it’s not a guarantee of anonymity. The internet device you connect to must record or log your IP address to be able to properly send the data back to you, so anyone able to access these records can uncover information about you.

It is much better to use the paid VPNs which provide a lot more features and assure/ promise not to store or log any of the information so that they won't be able to give your information to the security or intelligence firms even on getting forced as they don't your information themselves. In this way, if someone insists that the VPN service provider turn over its data to its user, there is no data.

# Encrypted Email

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697038633613/cfe9a200-80f7-4ff8-a60a-853fe8148d70.jpeg align="center")

Free commercial email services such as Gmail, Yahoo!, and Outlook Web Mail (formerly Hotmail) are free for a reason: they are vehicles for tracking your interests and serving up advertisements. As mentioned already, if a service is free, you are the product, not the customer. In addition, the servers of the email provider (Google, for example) have access to the unencrypted contents of your email, even if you’re using HTTPS.

One way to prevent eavesdropping on your email is to use encrypted email. ProtonMail encrypts your email from end to end or browser to browser. This means that your email is encrypted on ProtonMail servers—even the ProtonMail administrators can’t read your email.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697039259891/ada1e914-d368-4e85-bb8b-a8d04d643f3d.jpeg align="center")

ProtonMail was founded by a group of young scientists at the CERN supercollider facility in Switzerland. ProtonMail’s servers are based in the European Union, which has much stricter laws regarding the sharing of personal data than the United States. When exchanging email with non-ProtonMail users, there is the potential for some or all of the email not to be encrypted.

# Proxy Server

<mark>proxies</mark> are intermediate systems that act as middlemen for traffic: the user connects to a proxy, and the traffic is given the IP address of the proxy before it’s passed on. When the traffic returns from the destination, the proxy sends the traffic back to the source. In this way, traffic appears to come from the proxy and not the originating IP address.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697038702987/13d1d89c-adbe-4510-941b-e44919f93040.png align="center")

The proxy will likely log your traffic, but an investigator would have to get a subpoena or search warrant to obtain the logs. To make your traffic even harder to trace, you can use more than one proxy, in a strategy known as a **<mark>proxy chain</mark>**.

**<mark>proxychains</mark>** that you can set up to obscure your traffic. The syntax for the proxychains command is straightforward:

```bash
proxychain <the command you want proxied> <arguments>
```

If you wanted to use proxychains to scan a site with nmap anonymously:

```bash
proxyxhain nmap -sT -Pn <IP address>
```

This would send the nmap –sS stealth scan command to the given IP address through a proxy. The tool then builds the chain of proxies itself, so you don’t have to worry about it.

### Setting Proxies in the Config File

In this section, we set a proxy for the proxychains command to use. As with nearly every application in Linux/Unix, configuration of proxychains is managed by the config file—specifically /etc/proxychains.conf

We can add proxies by entering the IP addresses and ports of the proxies we want to use in this list. For now, we’ll use some free proxies. Note, however, that using free proxies in real-life hacking activity is not a good idea.

It’s important to note that proxychains defaults to using Tor if you don’t enter any proxies of your own. If you’re not adding your proxies and want to use Tor, leave this as it is. If you are not using Tor, you’ll need to comment out this line (add a # before).

As much as I like Tor, as mentioned, it is usually very slow. Also, because the NSA has broken Tor, I am much less likely to depend on it for anonymity. I therefore comment out this line and add my own set of proxies.

### Dynamic Chaining

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697038863422/bff2a483-b903-430f-8c68-073258a0e3af.png align="center")

With multiple IPs in our proxychain.conf file, we can set up dynamic chaining, which runs our traffic through every proxy on our list and, if one of the proxies is down or not responding, automatically goes to the next proxy in the list without throwing an error. If we didn’t set this up, a single failing proxy would break our request.

This will enable dynamic chaining of our proxies, thus allowing for greater anonymity and trouble-free hacking. Save the config file and feel free to try it out.

### Random Chaining

Our final proxy trick is the random chaining option, where proxychains will randomly choose a set of IP addresses from our list and use them to create our proxy chain. This means that each time we use proxychains, the proxy will look different to the target, making it harder to track our traffic from its source. This option is also considered “dynamic” because if one of the proxies is down, it will skip to the next one.

### Disadvantages

**<mark>proxychains</mark>** are only as good as the proxies you use. If you are intent on remaining anonymous, do not use a free proxy, as mentioned earlier. Hackers use paid-for proxies that can be trusted. In fact, the free proxies are likely selling your IP address and browsing history.

Although the IP address of your traffic leaving the proxy will be anonymous, there are other ways for surveillance agencies to identify you. For instance, the owner of the proxy will know your identity and, if pressured enough by espionage or law enforcement agencies with jurisdiction, may offer up your identity to protect their business. It’s important to be aware of the limitations of proxies as a source of anonymity.

Hope you get to find a lot of knowledge and data, you came to read this blog, soon I will be releasing blogs on managing and Analyzing Networks, Using & Abusing Services and a lot more..😎😎

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697040184335/48b7a110-cec7-4230-9380-f84212a7e514.gif align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[Aryan\_2407](https://twitter.com/Aryan_2407)