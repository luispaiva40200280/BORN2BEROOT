---
description: What are package mangers and the difference between  apt and AppArmor
cover: ../../../.gitbook/assets/Jiraiya _ Naruto Shippuden.jpeg
coverY: 117.17894736842106
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

# 👨‍💼 Package managers

> [!info]
> **APT** is the **package management system** used in Debian and its derivatives (like Ubuntu).\
> It handles installing, upgrading, and removing software from repositories.
> 
> **AppArmor** is a **Linux security module** that controls what applications are allowed to do.\
> It uses **profiles** to restrict each program’s access to files, network, and system resources.


Now after completing the LVM\`s we will configure the package manager of our operating system. On the first message that appears we click "no"&#x20;

<figure><img src="../../../.gitbook/assets/imagem (25).png" alt=""><figcaption></figcaption></figure>

Then we choose the country that we are in. Then we choose `deb.debian.org` as is the recommended by Debian itself. In the HTTP proxy we can leave blank. Then we refuse sending the statics of our system to the developers.

Also we will left in blank all software choices (with the space bar) and click on `Continue.`

Then we install the GRUB boot loader

<figure><img src="../../../.gitbook/assets/imagem (26).png" alt=""><figcaption></figcaption></figure>

After we choice the device `/dev/sda (ata_VBOX_HARDDISK)` for the installation for boot loader. And then we just continue&#x20;

<figure><img src="../../../.gitbook/assets/imagem (27).png" alt=""><figcaption></figcaption></figure>

&#x20;

> [!success]
> <mark style="color:$success;">Now our system is finish</mark>&#x20;

