+++
title = "Docker Deployment of FastAPI project"
#description = "Description of my awesome project."
date = 2022-11-17T02:13:50Z
author = "Ankit Singh"
+++

## Introduction
In this tutorial, we’ll configure a fastAPI based project with docker and deploy it to DigitalOcean using ubuntu.


## Prerequisite

* docker installation set up- ​​https://docs.docker.com/compose/install/.

* Installed Ubuntu version 18.0.4 

* Secure Shell (SSH) enabled user

* Installation of Nginx on Ubuntu 18.04 - Follow this
### Step 1 — Set up FastAPI project inside Docker container
Before directly jumping into the first step, just make sure that you already have installed docker desktop application on your computer.

* Now in the same project directory create a file Dockerfile with:

to know about each components here refer to fastAPI in Docker

{{< highlight html >}}

FROM python:3.10.7

WORKDIR /code

COPY ./requirements.txt /code/requirements.txt

RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt

COPY ./app /code/app

CMD ["uvicorn", "app.main:app", "--proxy-headers", "--host", "0.0.0.0", "--port", "80"]

{{< /highlight >}}

* Now Create a docker-compose.yml file in the same directory - define docker compose file

{{< highlight html >}}

version: "3"

services:

web:

build: .

ports:

- "8000:8000"

{{< /highlight >}}

### Step 2 — Create a droplet on DigitalOcean and connect to remote server

Refer to this link - create a droplet from the DO control pannel

* DigitalOcean Droplets - DigitalOcean Droplets are Linux-based virtual machines (VMs) that run on top of virtualized hardware. Each Droplet you create is a new server you can use.

* Open the terminal on your machine and run the following command: ssh your_username@host_ip_address        

In my case - ssh root@159.89.163.38 

* Type password and hit Enter

![alt text](https://github.com/DesignString/designstring-tech-blogs/blob/main/content/post/images/ssh%20-enable.png?raw=true)


### Step 3 — Add and Run the project with docker compose
Navigate to the directory - cd /var/www

* Clone the project using the following command - 

* git clone https://github.com/DesignString/crypto-token-exchange.git

* cd crypto-token-exchange

* Build and run your app with Compose🔗 -  docker-compose up

![alt text](https://github.com/DesignString/designstring-tech-blogs/blob/main/content/post/images/ssh%20-enable.png?raw=true)


### Step 4 — NGINX Configuration

All NGINX configuration files are located in the /etc/nginx/ directory. The primary configuration file is /etc/nginx/nginx.conf.

Inside the configuration file create a new config file and configure it:

* To create a new config file - touch virtual-test.conf

* Run nano virtual-test.conf

* Configuration example 


Screenshot 2022-11-16 at 3.57.06 PM.png

* After setting the configure file save it and once again run the following command to reload the newly created config file and to restart the nginx server


sudo systemctl reload nginx

sudo systemctl restart nginx


  Now go the droplet section on DigitalOcean website and select the earlier created droplet, then go the networking page and create a custom inbound with the running port.
