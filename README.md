# ICT171 Cloud Server Project

## Student Details

Name: Aidan Macliver  
Student Number: 33401722  
Unit: ICT171 Introduction to Server Environments and Architectures  
Project: Cloud-hosted personal portfolio website  

## Project Overview

This project involved creating a cloud-hosted personal portfolio website using Infrastructure-as-a-Service. I used Amazon EC2 to deploy a Linux virtual server and installed Apache to host the website. The website is accessible online through a public IP address.

Website URL: http://15.135.138.233  
Public IP Address: 15.135.138.233  

## Cloud Provider

Cloud provider: Amazon Web Services  
Service used: Amazon EC2  
Operating system: Ubuntu Linux  
Web server: Apache  

## Server Setup

The EC2 instance was created using an Ubuntu Linux image. After launching the instance, I connected to the server using SSH and installed Apache.

Commands used:

```bash
sudo apt update
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo systemctl start apache2
sudo systemctl status apache2
