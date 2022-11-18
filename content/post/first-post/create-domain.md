+++
title = "Create a domain name & point to an IP address using BigRock and certbot"
tags = [
    "go",
    "golang",
    "templates",
    "themes",
    "development",
]
date = 2022-11-16T02:13:50Z
author = "Ankit Singh"
+++

## Introduction
In this guide, we are going to see how we can create a domain name with the existing IP address using BigRock

BigRock - BigRock is a web hosting platform that provide a wide range of hosting solutions

These are the steps that we have to follow in order to create a domain name :-

Register a domain on Bigrock -  User’s guide

Once done with the registration Process, please follow the below steps-

1. From the home page, click on you account name and go through the page visit my account, from there navigate to List/Search Orders via clicking on Manage Order, there you can see all the existing domains

  [alt-image]()
Screenshot 2022-11-16 at 7.02.57 PM.png

![alt text](https://github.com/DesignString/designstring-tech-blogs/blob/main/content/post/images/ssh%20-enable.png?raw=true)

2.  Now click on a  domain name and scroll down to the end, on the bottom left corner you can see Manage DNS inside DNS management section

Screenshot 2022-11-16 at 4.42.14 PM.png

3.  After clicking on that you will redirected to the admin area of that domain, now click on add record and create a new record with the IP address

Screenshot 2022-11-16 at 7.04.52 PM.png

 4. Install and cofigure certbot inside the remote server - Guide

* Run the command - certbot in the terminal after login into the server with SSH

* Type 2 to select Nginx Web Server plugin (nginx)

* A list of domain will be show up, select that specific domain and that’s it https has been enabled.

Screenshot 2022-11-16 at 4.55.45 PM.png

