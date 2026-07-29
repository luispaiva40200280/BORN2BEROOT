---
icon: rotate
cover: ../../../.gitbook/assets/conect.avif
coverY: -171.4105263157895
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

# Connecting our machines via ssh protocol

After completing the ssh protocol in our machine we can go to our VM manager (Oracle Virtual Box) , and change our network settings;

* To change the settings we need to click in settings of our machine :gear: and go to network and changing `Attach to` option to `Bridged Adapter`&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot from 2025-11-01 22-46-10.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot from 2025-11-01 22-46-59.png" alt=""><figcaption></figcaption></figure>

*   After that in our main machine "our PC" we open the terminal and use the command ssh username@\<host IP> -p 4242 and then we use the password of our virtual machine &#x20;

    * host IP (is the ip of our machine) ⇒ ⇒ `sudo hostname -I`  or in our scrip that we will create&#x20;
    * "username" -> is of _**your main user**_**&#x20;**<mark style="color:$danger;">**not the root**</mark>&#x20;

    <figure><img src="../../../.gitbook/assets/Screenshot from 2025-11-01 23-03-02.png" alt=""><figcaption></figcaption></figure>

&#x20;                        :warning: <mark style="color:$warning;background-color:$warning;">**Remember your machine needs to be open for this to work**</mark>     :warning:  &#x20;

{% hint style="success" %}
<mark style="color:$success;">**After having the SSH connection complete we can do all the next steps in our terminal, that will facilitate quite a lot our life**</mark>
{% endhint %}

