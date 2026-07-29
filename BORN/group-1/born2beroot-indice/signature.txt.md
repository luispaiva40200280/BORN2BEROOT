---
description: >-
  To obtain the signature, the first thing we must do is shut down the virtual
  machine, since once you turn it on or modify something, the signature will
  change.
cover: >-
  ../../.gitbook/assets/Lost in the little moments 🎧✨, Music, memories, and the
  quiet comfort of home__._._._._._._._._.jpeg
coverY: -83.28421052631579
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

# ✒️ Signature.txt

1. The next step will be to locate ourselves in the path where we have the .vdi of our virtual machine. From our physical machine.
   1. Finally, we will run shasum "<mark style="color:$primary;">machinename</mark>".vdi and this will give us the signature. The result of this signature is what we will need to add to our signature.txt file and subsequently upload the file to the intra repository. It is very important not to reopen the machine since the signature will be modified. For corrections, remember to clone the machine so you can turn it on without fear of changing the signature.

```batch
shasum machinename.vdi
```

{% hint style="info" %}
<mark style="color:blue;">shasum</mark>: It is a command that allows you to identify the integrity of a file using the [SHA-1](https://en.wikipedia.org/wiki/SHA-1) hash check sum of a file.
{% endhint %}

{% hint style="warning" %}
<mark style="color:$danger;">**Remember that since once you turn it on or modify something, the signature will change.**</mark>
{% endhint %}
