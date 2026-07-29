---
icon: ban
cover: ../../../.gitbook/assets/protect.avif
coverY: 136.54736842105265
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

# UFW and allowing porting

{% hint style="info" %}
#### what is a firewall and what is ufw ?&#x20;

A **firewall** is a **security system** that controls **incoming and outgoing network traffic** based on a set of **rules**.

It acts like a **gatekeeper** between your computer (or network) and the outside world 🌐.

**UFW** stands for **Uncomplicated Firewall**.\
It’s a **user-friendly tool** for managing the **IP-tables** firewall on Linux (used in Debian, Ubuntu, etc.).

Think of it as a **simpler interface** to control complex firewall rules.
{% endhint %}

#### Now is time to install UFW&#x20;

* Using the command  <mark style="color:$success;">sudo</mark> <mark style="color:$warning;">`apt install ufw`</mark>  and when prompted for confirmation, type `y` and press Enter. The installation will proceed.
* **Enable the firewall:** Once the installation is complete, we need to enable UFW:&#x20;

```sh
sudo ufw enable
```

This command will activate the firewall. You should see a message confirming that the **firewall is active**.

#### Then we allow porting on the firewall

```sh
sudo ufw allow 4242
```

```sh
sudo ufw status
```

### &#x20;🔐 <mark style="color:orange;">Sudo policies</mark>&#x20;

<mark style="color:$warning;">Beginning with this section, we will create a file in /etc/sudoerd.d/ . The file will serve the purpose of storing our sudo policy.</mark>

* first we will create the file  "sudo\_config"

```sh
touch /etc/sudoers.d/sudo_config
```

* Then we must create a directory as is asked in the subject in _/var/log/_ because each commands need to be logged, the input and output

```sh
mkdir /var/log/sudo
```

* We must edit the file that we created in the first step of this section. <mark style="color:$info;">We can use any text editor if we have it but nano is already install so is we don´t need to have more trouble to install any more stuff</mark> &#x20;

```shell
(sudo) nano /etc/sudoers.d/sudo_config
```

* With the file opened we need to add the roles for the password that are asked in the subject

<pre class="language-shell" data-overflow="wrap"><code class="lang-shell">Defaults  passwd_tries=3
<strong>Defaults  badpass_message="Mensaje de error personalizado"
</strong><strong>Defaults  logfile="/var/log/sudo/sudo_config"
</strong>Defaults  log_input, log_output
Defaults  iolog_dir="/var/log/sudo"
<strong>Defaults  requiretty
</strong>Defaults  secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
</code></pre>

#### Setting up basic password aging&#x20;

* **Edit login definitions:** First, we need to edit the login.defs file:

```shell
nano /etc/login.defs
```

* **Modify password parameters:** Locate and change the following parameters in the file:

> Change: `PASS_MAX_DAYS 99999` → `PASS_MAX_DAYS 30`

> Change: `PASS_MIN_DAYS 0` → `PASS_MIN_DAYS 2`

> PASS\_WARN\_A&#x47;**:**  <mark style="color:$info;">does not need to be change probably</mark>&#x20;

* After changing the file we need to install a <mark style="color:$warning;">**password quality enforcement.**</mark>  Type `Y` when prompted to confirm and wait for the installation to complete.

```shell
sudo apt install libpam-pwquality
```

* **Configuring password complexity rules**
  * **Edit PAM configuration:** Next, we need to edit the PAM (Pluggable Authentication Modules) configuration file:

```sh
(sudo) nano /etc/pam.d/common-password
```

* Below **retry=3** we must add the following commands:

{% code overflow="wrap" %}
```sh
minlen=10 ucredit=-1 dcredit=-1 lcredit=-1 maxrepeat=3 reject_username difok=7 enforce_for_root
```
{% endcode %}

{% hint style="info" %}
<mark style="color:$primary;">minlen</mark><mark style="color:$success;">=</mark>10 ➤ <mark style="color:$info;">The minimum characters a password must contain.</mark>

<mark style="color:$primary;">ucredit</mark>=-1 ➤ <mark style="color:$info;">The password must contain at least one capital letter.</mark>&#x20;

<mark style="color:$primary;">dcredit</mark>=-1 ➤ <mark style="color:$info;">The password must contain at least one digit.</mark>

<mark style="color:$primary;">lcredit</mark>=-1 ➤ <mark style="color:$info;">The password must contain at least one lowercase letter.</mark>

<mark style="color:$primary;">maxrepeat</mark>=3 ➤ <mark style="color:$info;">The password cannot have the same character repeated three consecutive times.</mark>

<mark style="color:$primary;">reject\_username</mark> ➤ <mark style="color:$info;">The password cannot contain the username within itself.</mark>

<mark style="color:$primary;">difok</mark>=7 ➤ <mark style="color:$info;">The password must contain at least seven different characters from the last password used.</mark>

<mark style="color:$primary;">enforce\_for\_root</mark> ➤ <mark style="color:$info;">We will implement this password policy for root.</mark>
{% endhint %}

