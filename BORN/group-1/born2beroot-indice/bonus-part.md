---
description: >-
  Let`s challenge the bonus part of this project, this part consist in creatine
  a database and connecting it with our main machine via wordpress
cover: ../../.gitbook/assets/Cubone x Ghibli art.jpeg
coverY: 40.480000000000004
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

# ☠️ --- BONUS PART ---

#### :bulb:Lighttpd

> [!success]
> <mark style="color:$success;">Lighttpd</mark>: is a web server designed to be fast, secure, flexible, and standards-compliant. It is optimized for environments where speed is a top priority because it consumes less CPU and RAM than other servers.


* Lets install the service as usual&#x20;

```sh
sudo apt install lighttpd
```

* Lets allow the ports that need to be open for this service to be connected to our machine and check if it connects

```sh
sudo ufw allow 80
sudo ufw status
```

#### :newspaper: WordPress

> [!success]
> <mark style="color:$success;">**WordPress**</mark>: It is a content management system focused on the creation of any type of website.
> 
> <mark style="color:$success;">**wget**</mark>: It is a command line tool used to download files from the web.
> 
> <mark style="color:$success;">**zip**</mark>: It is a command line utility for compressing and decompressing files in ZIP format.


* To install the latest version of WordPress we must first install wget and zip

```
sudo apt install wget zip
```

* Now we can install the WordPress  ⇒ ⇒  it can be this  "[https://es.wordpress.org/latest-es\_ES.zip](https://es.wordpress.org/latest-es_ES.zip)"  or this "[https://pt.wordpress.org/latest-pt\_PT.zip](https://es.wordpress.org/latest-es_ES.zip)" depending of the language that you want
  * &#x20; Be sure to install the latest version of wordpress in the right path&#x20;

```shell
cd /var/www/
sudo wget https://pt.wordpress.org/latest-pt_PT.zip
sudo unzip latest-pt_PT.zip 
```

* Next it\`s time to rename the folders that we unzip and give all the correct permissions to the files on HTML folder&#x20;

```sh
sudo mv html/ html_old/
sudo mv wordpress/ html
sudo chmod -R 755 html
```

#### <i class="fa-database">:database:</i> **MARIADB**

> [!success]
> <mark style="color:$success;">**MariaDB**</mark>: It is a database. It is used for various purposes, such as data warehousing, e-commerce, enterprise-level functions, and logging applications.


* We will install the packages to our MariaDB database with the command

```sh
sudo apt install mariadb-server
```

> [!warning]
> <mark style="color:$warning;">**Check that the database is already protected, and if not, look up how to secure it.**</mark>


* Lets create a database for our wordpress site &#x20;
  * First lets open MariaDB with the command >> `mariadb`
  * Now inside lets create our database for our WP >>  `CREATE  DATABASE wp_database;`
  * And check if it is created >> `SHOW DATABASES ;`&#x20;
  * Next we need to create a user inside the database. We will use the command >> `CREATE USER 'username'@'localhost' ;`
  * And grant him access to the DATABASE >> `GRANT ALL PRIVILEGES ON wp_database.* TO 'username'@'localhost';`
  * `FLUSH PRIVILEGES;`
  * After we can `EXIT;` the MariaDB;

#### PHP&#x20;

> [!info]
> <mark style="color:blue;">PHP</mark>: It is a programming language. It is mainly used to develop dynamic web applications and interactive websites. PHP runs on the server side.


*   We install the necessary packages to be able to run web applications written in PHP language and that need to connect to a MySQL database. Run the following command:

    ```shell
    sudo apt install php-cgi php-mysql
    ```

#### :newspaper:WordPress 2nd take

* Access the /var/www/html directory and copy the wp-config-sample.php to wp-config.php and edit the values corresponding to your database data

```sh
cd /var/www/html
cp wp-config-sample.php wp-config.php
(sudo) nano wp-config.php
```

* Inside the file we change the values of our "database name" our "user name" and our "password"&#x20;
  * Username: is the user that as privileges in the database;
  * Password: if we din\`t create a password on the user or database we put it empty;

<figure><img src="../../.gitbook/assets/imagem (34).png" alt=""><figcaption></figcaption></figure>

* We enabled the fastcgi-php module in Lighttpd to improve the performance and speed of web applications on the server:

```sh
sudo lighty-enable-mod fastcgi
```

* We enabled the fastcgi-php module in Lighttpd to improve the performance and speed of PHP-based web applications on the server:

```sh
sudo lighty-enable-mod fastcgi-php
```

* We update and apply the changes in the configuration with the command:

```sh
sudo service lighttpd force-reload
```

#### Now inside of our host

* &#x20;We open our browser and in the search bar we digit our machine IP address   and our wordpress website is already running&#x20;

<figure><img src="../../.gitbook/assets/Screenshot from 2025-11-02 21-50-07.png" alt=""><figcaption></figcaption></figure>

#### :cloud\_lightning: LiteSpeed

> [!success]
> <mark style="color:$success;">**LiteSpeed**</mark>: It is a proprietary web server software. It is the fourth most popular web server, and is estimated to be used by 10% of websites.
> 
> <mark style="color:$info;">**By default, OpenLiteSpeed is available in the Debian 11 base repository. So, you must run the following command to add the OpenLiteSpeed repository to your Debian system:**</mark>


* Before installing any software, it is important to ensure that the system is up to date and upgrade:

```sh
sudo apt update
sudo apt upgrade
```

* Lets Install the LiteSpeed web server repository and OpenLitespeed &#x20;

```sh
wget -O - https://repo.litespeed.sh | sudo bash
sudo apt install openlitespeed
```

* We configure the firewall to allow connections through ports 8088 and 7080.&#x20;

```shell
sudo ufw allow 8088/tcp
sudo ufw allow 7080/tcp
sudo ufw reload
```

* Once we have completed the previous step we can connect. We will put in the search engine of our browser `<IP address>:7081` we provide our login credentials and we will have access to everything.

> [!info]
> <mark style="color:$info;">**If your browser does no let you open the web page because is unsafe you can just ignore that and forcebly enter the website**</mark>


<figure><img src="../../.gitbook/assets/Screenshot from 2025-11-02 22-02-12.png" alt=""><figcaption></figcaption></figure>

* After inserting the credentials we can see the <mark style="color:$success;">**LiteSpeed**</mark> service&#x20;

<figure><img src="../../.gitbook/assets/Screenshot from 2025-11-02 22-05-41.png" alt=""><figcaption></figcaption></figure>

### Why Some Choose LiteSpeed

1. **It’s a web server**, which fits the “install a service” requirement.
2. It’s easy to install and configure.
3. It has a **web interface** (which can help you show configuration and monitoring).
4. It’s **lightweight** and performs well with minimal setup.
5. It supports **systemd**, so you can demonstrate service management (`systemctl start|stop|status lsws`).

> [!warning]
> When cloning the machine we need do clone it we need to change the option of <mark style="color:yellow;">**MAC Address Policy of**</mark> <<mark style="color:$warning;">Include only NAT network adapter MAC addresses</mark>> to <<mark style="color:$success;">Include all network adapter MAC addresses</mark>>


> [!success]
> &#x20;                                                                    <mark style="color:$success;">**Now Born2beroot is complete**</mark>&#x20;

