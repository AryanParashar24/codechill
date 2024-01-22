---
title: "Hack🥷the Wi-Fi & Router with Kali🐉, Flipper-Zero and Wi-Fi Pineapple🍍"
seoTitle: "Hack🥷the Wi-Fi & Router with Kali🐉, Flipper-Zero and Wi-Fi Pineapple"
seoDescription: "Now in this blog, I will be sharing some introductory methods and some special tools being used by these hackers like Flipper-0 and Wi-Fi Pineapple."
datePublished: Mon Jan 22 2024 12:14:02 GMT+0000 (Coordinated Universal Time)
cuid: clrow2yci000c08l542c7g5eh
slug: hackthe-wi-fi-router-with-kali-flipper-zero-and-wi-fi-pineapple
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705682518157/4b8e83e0-1791-480b-907c-123c50641c40.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1705925597035/06cc3ab5-ade7-4718-b4ff-717ab4fd4cdb.jpeg
tags: software-development, security, hacking, networking, cybersecurity-1

---

We all dreamt about hacking and being cool in front of other people after seeing scenes from the movies and tv serial. Everyday in the newspaper, we have seen the cases where the individuals or groups hacked into the network of some secured organizations which emerged a lot of projects to secure our networks and avoid any breach of information or data of our users, clients and employees. These cases also make us wonder (just out of curiosity), How do they do these people hack into these systems and get the information out of these systems.

Now in this blog, I will be sharing some introductory methods and some special tools being used by these hackers like Flipper-0 and Wi-Fi Pineapple. These methods will revolve around the practical way through Kali Linux and tools, how Hackers and attackers can establish a Man-In-The-Middle(MITM) Attack to get access to the information about the users and targets which are connected through some router or Wi-Fi.

Here we will be using Kali Linux as an introductory method in the first case. For Those who don't know about Kali Linux here are it's basic usage.

# Hack the Wi-Fi & Router

## Kali Linux

Kali Linux is a specialized Linux distribution designed for penetration testing, ethical hacking, and cybersecurity purposes. It is an open-source project that provides a collection of pre-installed powerful tools and utilities for various security tasks, including vulnerability assessment, penetration testing, digital forensics, and reverse engineering. Kali Linux is widely used by cybersecurity professionals, ethical hackers, and security enthusiasts. It is highly customizable, allowing users to install additional tools or remove unnecessary ones based on their specific needs.

Here are the commands which will be contributing in establishing a Man-In-The-Middle Attack (MITM) Attack.

```bash
sudo bettercup -iface eth0
```

[Bettercap](https://www.bettercap.org/) is a powerful, modular, and portable penetration testing framework that focuses on network attacks and man-in-the-middle (MITM) techniques. It acts as The Swiss Army knife for [WiFi](https://www.bettercap.org/modules/wifi/), [Bluetooth Low Energy](https://www.bettercap.org/modules/ble/), wireless [HID hijacking](https://www.bettercap.org/modules/hid/) and [IPv4 and IPv6](https://www.bettercap.org/modules/ethernet) networks reconnaissance and MITM attacks.

* `bettercap`: This is the main command for launching Bettercap.
    
* `-iface eth0`: This option specifies the network interface to use for network-related activities. In this case, it's set to `eth0`, which is a common designation for the first Ethernet interface on a Linux system. You may need to replace `eth0` with the appropriate interface on your system.
    

```bash
net.probe on
```

To scan the current Wi-Fi network and find targets connected to the Wi-Fi we are connected.

```bash
net.show
```

To see what the computer founded after scanning the current Wi-Fi network.

```bash
set arp.spoof.fulldeplex true
```

To set up his `arp` by setting it to full duplex mode. Now here in this method we will be using the `arp spoofing` to establish the MITM attack, to get access to the information and targets' data connected to the internet.

---

### arp Spoofing

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705925399320/f14fee04-f92b-4237-8628-fd7d2cd7c324.png align="center")

ARP (Address Resolution Protocol) spoofing is a network attack where an attacker sends falsified ARP messages over a local area network (LAN). The primary goal of ARP spoofing is to associate the attacker's MAC (Media Access Control) address with the IP address of a legitimate network device. This association is stored in the ARP cache of the target devices, leading to potential security vulnerabilities.

**Address Resolution Protocol (ARP):**

ARP is a protocol used to map an IP address to a physical MAC address on a local network. Devices use ARP to discover the hardware address associated with a given IP address.

**ARP Spoofing Working model:**

1. The sender (initiator) broadcasts an ARP request packet to the entire local network. Legitimate devices with the matching IP address reply with their MAC addresses.
    
2. The attacker sends forged ARP reply packets to the target device, claiming to be the device with the sought-after IP address. The forged packet includes the attacker's MAC address as the response to the ARP request. The target device, trusting ARP responses, updates its ARP cache, associating the attacker's MAC address with the IP address it was seeking.
    
3. The target device now has an incorrect entry in its ARP cache, associating the attacker's MAC address with the legitimate IP address, when the target device wants to communicate with the legitimate device, it sends data to the attacker's MAC address, thinking it is the correct destination, this is known as the ARP Cache poisionning.
    
4. With the ARP cache poisoned, the attacker is in a man-in-the-middle position. The attacker can intercept, modify, or drop the traffic passing between the legitimate devices.
    

---

Now, we know what do we mean by the arp spoofing and now we can proceed with the further steps in the process.

```bash
set arp.spoof.fulldeplex true
```

Here in this command, the `arp.spoof.fulldeplex` parameter relates to ARP spoofing, which is a technique used in network attacks to intercept network traffic. ARP spoofing involves sending fake ARP (Address Resolution Protocol) messages to associate the attacker's MAC address with the IP address of a legitimate network device.

Now we can specify the target within the network through the command as:

```bash
set arp.spoof.targets IP_Address
```

Now, further we would be commanding the `arp.spoof on` btu before it we will open up the package capture program called **Wire Shark.**

### Wire Shark

With **Wire Shark,** we can capture everything it is seeing going across the network and because all the network between the target and router are going through hacker, which will be a lot in numbers.

Select the `capture/ tracking` type which is `wlan0` in our case then, we can fill `ip.src==IP_ADDRESS` in the search bar.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705924799693/1c4f70b1-5dfb-438d-b489-8bad8a368ce5.png align="center")

Now, we can proceed to switching on the arp.spoof as:

```bash
arp.spoof on
```

Now, here we will be able to see every activity and the site being visited by the user while accessing the internet through the router which also connects the attacker and the target to the internet.

### Precautions

To save ourselves from such kind of MITM attacks, we can use the VPNs like Nord VPN to resist any such kind of breach of information or data of users and clients from the MITM attack.

After setting the VPN on, every activity will look same and nothing will be able to get uncovered for the attackers, saved by the VPNs and protocol will be set to WireGaurd with every packet and data packet being encrypted and hidden between our target and one destination from the attacker.

## Evil Twin Attack

Here it is an attack, where let's say our target is in a cafe where the password is also provided to be used. Our hacker would provide another cloned network connection with the same password so that users can get connected to him instead.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705925465788/6953a801-e124-49a2-9d69-47be2ef15b68.jpeg align="center")

To perform this task setting up a personnel router would be really tedious so instead, hacker would be caring a Flipper-Zero with him, which will be connected to the ESP32 den board or a Wi-Fi dev board flash with the Marauder firmware, enabling the Flipper-Zero to do an attack.

Then the hacker can connect his phone to control Flipper-Zero and the application will enable the Evil Twin along with an Evil portal.

**<mark>Evil Portals</mark>** are the twin portal to the verifying or the gateway websites, some network connections has to sign-in or log-in to connect through google sign-in or hotel room number, etc and then the innocent users without getting to know whom do they are connected that will just put on their credentials like passwords and emails, then will give them away to the Hacker.

**Disadvantages of Flipper-Zero:**

Now this may give the credentials pf the users to the attacker but, since they don't offer an actual internet connectivity thus users and target will get disconnected at some point thus attacker may get access to the credentials but can't get the continous flow of information and request history.

## Wi-Fi Pineapple

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705924826666/db1e8c49-cd05-48af-9b02-1c25345c5209.png align="center")

Now, here comes the pro method where a hacker comes with the Wi-Fi Pineapple instead of a Flipper-Zero. It will get connected to the user and controlled through an interface or application where it will enable **Evil-Twin** and portal will just click once, thus will be able to connect easily. He will scan up the entire wireless network. These produce a strong signals thus get connected to them . So it is easier for an attacker to have stronger signal than anything else through that spider looking device.

The best feature is that sometimes the connection get compromised and get disconnected when we got out of the reach or we do have a nice 5g network connection with us so we didn't decided to connect with the router, but with Wi-Fi Pineapple we will get to exercise an amazing feature with which, we can listen to those probes with which target had an earlier connection.

We all have connected to some other network connection at our home, work or public space like a cafe, airport or metro station thus, all of those information about the network connection is saved within our devices so that next time whenever we come into the domain of those network connections then our devices can get connected to those network connections without getting to fill up the password and log-in again, thus our devices got auto-connected to those network connections.

So this spider looking device i.e. Wi-Fi Pineapple find these early remembered connectivities, clone them and push them to users with a stronger signal. It will listen to those probes to catch those wireless connection history our phone remembers to whom it got connected in past. The Wi-Fi Pineapple grab them, make a clone of them and then broadcast it which the phone connects automatically to the hacker's network.

it grabs all the Wi-Fi networks it can find and broadcast those, casting a vast and wide net catching whatever it can handle.

## Back to Kali Linux

Now, after we have installed driver and installed few tools. We may use a tool called DNS Mask to run DHCP.

```bash
nano dnsmasq
```

The command `nano dnsmasq` is used to open the configuration file for the `dnsmasq` service using the `nano` which is a command-line text editor with a user-friendly interface.

`dnsmasq` is a lightweight and versatile DNS (Domain Name System) forwarder and DHCP (Dynamic Host Configuration Protocol) server. It can be used to provide DNS resolution services and assign IP addresses to devices on a local network.

The above command help to handle out IP address and to run DNS which will help our target to actually reach websites on the internet.

```bash
nano hostpad.conf
```

It will launch a wireless network, attacker might match the SSID and a channel sname to be the exact same so that anyone can accidently connect to it and then they can do whatever they want like spoofing your DNS.

**<mark>Detailed explanation</mark> :**

When we go to visit a website then our computer has no idea how to reach the destination so it hooks for an IP address somewhere in the data center. So facebook.com or google.com is just a friendly name so that we don't have to write the whole IP address in our URL bar.

**<mark>DNS Lookup</mark> :**

DNS servers are easier where request will go to the DNS server and will handle back the requested website. This happen for every website we ever request for whether it could be facebook.com, youtube.com, google.com, etc.

Hacker can now make DNS server respond in any way it wants. So when the target asked or requested for any website to the DNS server which is our computer in this case and we can decide which website as the response give back to the target like our own website to get traffic or a fake clown to perform any specific malicious tasks.

This attack is called is called **DNS Spoofing** and thus an attacker can do crazy stuff diverting you to some other websites, send you messages, get access to your web cam.

<mark>Protection</mark>

As a protection we may use a VPN like a Nord VPN or other VPNs which may provide certain specific/ special protection like Double VPN, Onion over VPN.

# Crack the Wi-Fi Password

**<mark>For Kali Linux</mark>**

```bash
sudo airmon-ng wlan0 start
```

This command is use to put alpha network adapters which allows his Wi-Fi adapters instead of just connecting to a wireless network network and we can listen or attack with actions like a DAuth attack.

### DAuth Attack

A death or D-Authentication attack disrupts connection between users and Wi-Fi access points. the attackers force devices to loose access and then re-connected to a network they control. Then parpetrator can track connections, capture login details, or trick users into installing rogue programs.

So in this attack an attacker can force any phone, laptop or any other device on wireless network to loose it's connection de-authentication from wireless network.

Now after using the `iwconf` to get teh details about the IP address, MAC address, IPV4 and IPV6 addresses of our systems.

```bash
sudo airmon-ng check kill
```

To check and kill those processes running in the background.

```bash
sudo airdump-ng wlan0 -abg
```

To start the monitoring for all types of wireless channels and now we can see everything all the wireless networks accessing.

```bash
sudo airdump-ng-bssid MAC_Address -c 2 wlan0
```

`airdump-ng` is a set of tools for auditing wireless networks. `airdump-ng` is specifically used for packet capturing and network reconnaissance.

`-c 2`specifies the channel number to capture traffic on. In this case, it's set to channel 2. You can replace `2` with the channel number of the target AP. This helps focus the capture on a specific channel.

`wlan0` is used for capturing packets. `wlan0` is a common designation for a wireless network interface on Linux systems. You may need to replace it with the appropriate interface on your system.

```bash
sudo airplay-ng -0 0 -a MAC_Address wlan0
```

Through this attackers can target one individual person that he scanned and recon or the entire network and all clients get de-authenticated all at ones and soon he does it, he got captured a 4 way handshake when they try to reconnect and soon as he sees EAPOL message and then he proceed to crack the password.

**<mark>De-Auth with the Flipper-Zero:</mark>**

Through out Flip-Zero connected phone application, we can launch the de-auth, start capturing packages and captured a four-way handshake.

**<mark>De-Auth with the Wi-Fi Pineapple:</mark>**

We can enable scanning for the pineapple interprise through interface, which will automatically start receiving all handshakes and with few clicks, we can de-auth any network and their clients seamlessly within moments.

Now, these all will end up with a packet capture file with a four way handshake. Although we got more to get password but we have ingredients for it. Now, Hacker get to guess a lot to see if that can can decode the messages in the four way handshake and for this we can use the software like **rockyou.txt.gz** to make a lot for guessing over and over again until we find it.

```bash
sudo aircrack-ng -w/usr/share/wordlists/rockyou.txt getthathash-01.cap
```

```bash
ll /usr/share/wordlists
```

We need a bag or list of words/passwords wordlist contain a ton of passwords, so he will extract them using the above command which can be used to find location of files/ folders in system.

## Password guessing with Flipper-Zero & Wi-Fi Pineapple

Here in this command we will be using a tool called as the "**cewl**" to crawl the website of coffee shop to find all the keywords which might be used to password and output them as a list.

```bash
sudo cewl bearcravecoffee.com -w bearcave -passlist.text
```

Then we will use a tool called "**pipal**" which will look through the wordlist and find words that will probably really be used in a password. Identify the top 10 and then we can use some special Linux tool to put them into a nice and neat list to use in our next tool that we built ourselves or through the python list.

```bash
sudo pipal bearcave_passlist.txt | grep -A 10 "Top 10 passwords" | tail -n + 2 | awk -F '=' '{print $1}' | tr 'A-Z' 'a-z' top_10_passwords.txt
```

Here is the python script for getting ready the top 10 keywords for password guessing as:

```python
from itertool import product

input_file = 'top_10_passwords.txt'
output_file = 'bc_final_pwlist.txt'

with open(input_file, 'r') as f:
    words = [lene.strip() for line in f.readlines()]

words += [word.upper() for word in words]

with open(output_file, 'w')as f:
    for combo in product(words, repeat = 2):
        f.write(''.join(combo) + '\n')
```

Then we can move ahead to the following commands:

```bash
nano wlen.py
```

To open the file named [`wlen.py`](http://wlen.py) in the `nano` text editor.

```bash
python3 wlen.py
```

It will give more target list, taking lesser time, give higher odds of discussing the passwords.

```bash
sudo aircrack-ng -w bc_final_pwlist.txt getthat-01.cap
```

To run eth search and try command again to crack the password.

# Protection

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705924870333/459dd732-d7e5-466f-9043-5be44e093c91.png align="center")

As we have discussed earlier VPNs can be used for the protection of network and architecture of our system. Use of very strong random password got nothing to do with you. Nothing more can be done until we have a strong enterprise hardware.

There are enterprise Wi-Fi network out there that can do crazy things like they can do host isolation for all host connecting to your networks. So Man-In-The-Middle attack can not even happen. They can't talk to anyone else on that network. Even Twin Attacks are comparatively more difficult but a lot of smart enterprise wireless network can actually look for it's similar or same SSID as the networks, they are broadcasting, alert you or try to stop them with their own kind of Wi-Fi migration attacks.

Soon I will be publishing more about the networking models and dangerous Ransome tools like log4j Ransome attacks, AWS VPC and networking models and architecture & infrastructure.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705925246603/4960f9c9-4a49-442f-b8cb-5adc72f39c0d.png align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[**Aryan\_2407**](https://twitter.com/Aryan_2407)