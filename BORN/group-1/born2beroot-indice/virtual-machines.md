---
description: >-
  A compressive guide of how to do Born2BeRoot project!! Creating and
  configuring your first server using Virtual-box and Debian.
cover: >-
  ../../.gitbook/assets/Cute Pokemon Art_ Unveiling Adorable Masterpieces 2024
  187.jpeg
coverY: 221.09362786745965
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

# 👨‍💻 Virtual Machines

#### <sub><mark style="color:purple;">What is a virtual machine ?<mark style="color:purple;"></sub>&#x20;

> A **virtual machine** is a **software-based simulation of a physical computer,** basically  is like having a **computer inside a computer.** It acts as an isolated environment **that uses the host computer’s resources (CPU, memory, storage, etc.) but behaves as if it were a separate,** independent machine.

#### <mark style="color:purple;">How many types of virtual machines are ?</mark>

There are **two main types of virtual machines**, based on their purpose and how they interact with the system: _**but the one that bor2beroot is asking to do is of the first type.**_&#x20;

#### &#x20;<sub>**1. System Virtual Machines**</sub>

These provide a **complete virtualized environment** to run an entire operating system — just like a physical computer.

**🔹 Example:**

* Running **Linux** inside a **Windows** host using **VMware** or **Virtual-box**.
* Cloud VMs on **AWS EC2**, **Azure**, or **Google Cloud**.

**⚙ Characteristics:**

* Emulates full hardware (CPU, memory, storage, network).
* Each VM runs its own _guest OS_.
* Managed by a **hypervisor**.

:brain: **Common Hypervisors:**

* Type 1 (Bare-metal): VMware ESXi, Microsoft Hyper-V, KVM.
* Type 2 (Hosted): Virtual-box, VMware Workstation.

#### <sub>⚙</sub> <sub></sub><sub>**2. Process Virtual Machines**</sub>

These are designed to run a **single program or process**, not an entire OS.\
They abstract the execution environment for that program.

**🔹 Example:**

* **Java Virtual Machine (JVM)** → Runs Java byte-code on any system.
* **.NET Common Language Runtime (CLR)** → Runs .NET applications.

**⚙ Characteristics:**

* Exists only while the program runs.
* Provides platform independence for the application.
* Doesn’t emulate hardware; focuses on software execution.

#### <mark style="color:purple;">WHAT IS THE Virtual Box ?</mark>&#x20;

**Oracle VM Virtual-Box** (usually just called **Virtual-Box**) is a **free, open-source virtualization software** that lets you run **multiple operating systems** on a single physical computer at the same time. It’s one of the most popular tools for **creating and managing virtual machines (VMs)** on desktops and laptops.

*   Virtual-Box allows you to:

    * Create **virtual machines** on your computer (the **host**).
    * Install different **guest operating systems** inside those VMs — such as Windows, Linux, macOS, or others.
    * Run them **side by side**, as if you had multiple computers in one.



#### <mark style="color:purple;">Why choose the Debian OS and hat is an ISO file ?</mark>

An **ISO file** (or **ISO image**) is a **single file that contains an exact copy of all the data** on a CD, DVD, or other disk. It’s often used for **distributing operating systems** like **Debian or others.**

**Debian** is one of the oldest **Linux distributions**. It’s **stable, secure, and free** and a great choice for general users who want reliability and are new on this subject.
