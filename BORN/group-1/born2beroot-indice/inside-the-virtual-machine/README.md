---
description: >-
  In this page we will work inside our machine, installing all packages
  necessary for the project and creating or modifying the scrips
cover: >-
  ../../../.gitbook/assets/Bulbasaur animation illustration nintendo pokemon
  bulbasaur.gif
coverY: 0
layout:
  width: default
  cover:
    visible: true
    size: hero
    mask: none
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# 🎰 INSIDE THE VIRTUAL MACHINE

#### **After booting your machine and putting the passwords of the root and primary users we will start  the download of the necessary packages**

First in our "command line" we type `su` to change to the root user then **we install "sudo" using apt;** then we reboot our system, after we change again to the root user and confirm the sudo version&#x20;

1. `su`
2. `apt install sudo`&#x20;
3. `sudo reboot`&#x20;
4. `sudo -v`

After installing sud**o we create a user and a group called user42 ,** after we can check if the group is crated, after that we can add the user created or other user to the group user42 and the sudo group;

> <mark style="color:$primary;">" everything is done in the root user "</mark>&#x20;

1. `sudo adduser <login>`
2. `sudo addgroup user42`
3. `getent group`
4. `sudo adduser <username> <groupname>`   " we change the username and groupname depending on who an where we want to add   "
5. `getent group sudo <groupname>`

> [!info]
> ### 🧩 **What is `sudo`?**
> 
> `sudo` stands for **“superuser do.”**\
> It allows a **regular user** to **run commands with administrative (root) privileges** — temporarily giving them elevated access.


#### Now we start to install the ssh protocol

> [!info]
> <mark style="color:purple;">SSH</mark> stands for "Secure Shell." The SSH protocol was designed as a secure alternative to unsecured remote shell protocols. It utilizes a client-server paradigm, in which clients and servers communicate via a secure channel.


**We can before Installing OpenSSH server update the apt, then we can confirm our ssh server status**

1. `sudo apt update`
2. `sudo apt install openssh-server`
3. `sudo service ssh status`

After installing our ssh protocol we need to change it to be accessible in the port 4242 as it is required for the project&#x20;

1.  For that we need to open the file ssh\_config and changing the port and Disable root login via SSH:

    * Find: `#Port 22` Change to: `Port 4242`

    <figure><img src="../../../.gitbook/assets/imagem (30).png" alt=""><figcaption></figcaption></figure>

    * Find: `#PermitRootLogin prohibit-password` Change to: `PermitRootLogin no`&#x20;

<div align="center"><figure><img src="../../../.gitbook/assets/imagem (29).png" alt=""><figcaption></figcaption></figure></div>

* **Save the changes:** When finished editing, save the file and exit the editor (in Nano: `Ctrl+X`, then `Y`, then `Enter`). Now with the file `/etc/ssh/ssh_config`. (not `sshd_config`)

> <mark style="color:$info;">#Port 22 -> Port 4242</mark>

<figure><img src="../../../.gitbook/assets/imagem (31).png" alt=""><figcaption></figcaption></figure>

Then we need to restart and once it is done we will check the service state with:

* `sudo service ssh restart`
* `sudo service ssh status`

> [!success]
> <mark style="color:$success;">After that we can connect via ssh our virtual machine whit our host our main computer</mark>&#x20;


