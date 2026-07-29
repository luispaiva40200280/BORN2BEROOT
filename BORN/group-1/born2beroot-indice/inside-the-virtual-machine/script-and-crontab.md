---
description: >-
  Is very important that you look for what the flags stand for and what the
  script does
cover: ../../../.gitbook/assets/script.avif
coverY: -6.778947368421052
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

# ⌛ SCRIPT AND CRONTAB

{% hint style="danger" %}
<mark style="color:$danger;">**Do not cheat in this part!**</mark> <mark style="color:$warning;">You will be asked how the script works during the evaluation, so understand it as the evaluator expects.</mark>
{% endhint %}

{% hint style="success" %}
<mark style="color:$warning;">**script**</mark>: is a sequence of commands stored in a file that, when executed, will perform the function of each command.
{% endhint %}

* Bellow the scrip is a **brief explanation** of what we want to show with the script&#x20;

{% code fullWidth="true" %}
```sh
#!/bin/bash

# ARCH
arch=$(uname -a)

# CPU PHYSICAL
cpuf=$(grep "physical id" /proc/cpuinfo | wc -l)

# CPU VIRTUAL
cpuv=$(grep "processor" /proc/cpuinfo | wc -l)

# RAM
ram_total=$(free --mega | awk '$1 == "Mem:" {print $2}')
ram_use=$(free --mega | awk '$1 == "Mem:" {print $3}')
ram_percent=$(free --mega | awk '$1 == "Mem:" {printf("%.2f"), $3/$2*100}')

# Total disk space (in GB)
disk_total=$(df -m | grep '^/dev/' | grep -v '/boot' | awk '{total += $2} END {printf("%.1f", total/1024)}')
# Used disk space (in GB)
disk_used=$(df -m | grep '^/dev/' | grep -v '/boot' | awk '{used += $3} END {printf("%.1f", used/1024)}')
# Disk usage percentage
disk_percent=$(df -m | grep '^/dev/' | grep -v '/boot' | awk '{used += $3; total += $2} END {printf("%d", (used/total)*100)}')


# CPU LOAD
cpul=$(vmstat 1 2 | tail -1 | awk '{printf $15}')
cpu_op=$(expr 100 - $cpul)
cpu_fin=$(printf "%.1f" $cpu_op)

# LAST BOOT
lb=$(who -b | awk '$1 == "system" {print $3 " " $4}')

# LVM USE
lvmu=$(if [ $(lsblk | grep "lvm" | wc -l) -gt 0 ]; then echo yes; else echo no; fi)

# TCP CONNEXIONS
tcpc=$(ss -ta | grep ESTAB | wc -l)

# USER LOG
ulog=$(users | wc -w)

# NETWORK
ip=$(hostname -I)
mac=$(ip link | grep "link/ether" | awk '{print $2}')

# SUDO
cmnd=$(journalctl _COMM=sudo | grep COMMAND | wc -l)

wall "	Architecture: $arch
	CPU physical: $cpuf
	vCPU: $cpuv
	Memory Usage: $ram_use/${ram_total}MB ($ram_percent%)
	Disk Usage: $disk_use/${disk_total} ($disk_percent%)
	CPU load: $cpu_fin%
	Last boot: $lb
	LVM use: $lvmu
	Connections TCP: $tcpc ESTABLISHED
	User log: $ulog
	Network: IP $ip ($mac)
	Sudo: $cmnd cmd"
```
{% endcode %}

### Architecture <a href="#architecture" id="architecture"></a>

{% hint style="info" %}
The **architecture of an operating system** refers to the **overall design and structure** of how the OS is built
{% endhint %}

### Physical Cores <a href="#physical-cores" id="physical-cores"></a>

{% hint style="info" %}
A **physical core** is a **real, physical processing unit** inside your computer’s CPU.\
Each core can **execute its own tasks (threads)** independently.
{% endhint %}

### Virtual Cores <a href="#virtual-cores" id="virtual-cores"></a>

{% hint style="info" %}
A **virtual core** (or **logical core**) is a **simulated processing unit** that the operating system sees &#x20;

Is basically  a _software-visible thread_ that shares the resources of one **physical core** to perform more than one task at a time.
{% endhint %}

### RAM <a href="#ram" id="ram"></a>

{% hint style="info" %}
**RAM** stands for **Random Access Memory**.\
It’s your computer’s **short-term memory** — where data and programs are stored **temporarily** while they’re being used.
{% endhint %}

### Disk memory <a href="#disk-memory" id="disk-memory"></a>

{% hint style="info" %}
**Disk memory** (also called **storage** or **secondary memory**) is the **long-term memory** of your computer.\
It permanently stores your **files, programs, and operating system**, even when the power is off.
{% endhint %}

### CPU usage percentage <a href="#cpu-usage-percentage" id="cpu-usage-percentage"></a>

{% hint style="info" %}
**CPU** stands for **Central Processing Unit**.\
It’s the **main component** of a computer that **processes instructions** — basically, it’s what **makes your computer think and work**.
{% endhint %}

### TCP connections <a href="#tcp-connections" id="tcp-connections"></a>

{% hint style="info" %}
**TCP** stands for **Transmission Control Protocol**.\
It’s one of the main protocols used on the internet to **send and receive data reliably** between two devices.

A **TCP connection** is like a **phone call 📞** between two computers — both sides connect, talk reliably, and hang up properly when done.
{% endhint %}

### <mark style="color:blue;">Crontab</mark>&#x20;

{% hint style="info" %}
<mark style="color:$success;">**crontab**</mark>: is a background process manager. The specified processes will be executed at the time you specify in the crontab file.
{% endhint %}

* If we don\`t have the crontab install we can run this command

```sh
sudo apt update
sudo apt install cron
```

* To properly configure crontab, we must edit the crontab file with the following command:

```sh
sudo crontab -u root -e
```

In the file, we must add the following command for the script to execute every 10 minutes and in reboot/booting

```clike
@reboot sleep 40; sh /home/lpaiva/monitoring.sh
*/10 * * * * sh /home/lpaiva/monitoring.sh
```
