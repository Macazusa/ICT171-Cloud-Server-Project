# ICT171 Cloud Server Project

## Student Details

Name: Aidan Macliver
Student Number: 33401722
Unit: ICT171 Introduction to Server Environments and Architectures
Project: Cloud-hosted personal portfolio website

## Project Overview

This project involved creating a cloud-hosted personal portfolio website using Infrastructure-as-a-Service. I used Amazon EC2 to deploy a Linux virtual server and installed Apache to host the website. The website is accessible online through a public IP address.

The purpose of this project was to demonstrate how a website can be deployed, configured and managed on a cloud server rather than using local hosting or a Software-as-a-Service website builder.

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
```

## Security Group Configuration

The following inbound ports were configured:

| Port | Purpose                  |
| ---- | ------------------------ |
| 22   | SSH access               |
| 80   | HTTP web traffic         |
| 443  | Future HTTPS web traffic |

SSH was used for remote server administration. HTTP was enabled so the website could be publicly accessed from a browser. Port 443 was also allowed for future HTTPS configuration, although HTTPS was not fully configured at the time of submission.

## Website Deployment

The website was created using HTML, CSS and JavaScript. The completed `index.html` file was uploaded to the server using SCP and copied into the Apache web root directory.

Commands used:

```bash
scp -i "ICT171-aidan-key.pem" index.html ubuntu@15.135.138.233:/home/ubuntu/index.html
sudo cp /home/ubuntu/index.html /var/www/html/index.html
sudo systemctl restart apache2
```

The Apache web root directory used for this project was:

```bash
/var/www/html/
```

## Website Functionality

The website is a personal portfolio page that includes:

* An introduction section
* A skills section
* A cloud project description
* Student details
* A JavaScript feature section
* A dark mode button

The website is hosted on the EC2 instance and can be accessed using the public IP address.

## Scripting Component

The website includes JavaScript scripting features.

The first feature dynamically displays the current date and time on the website. The time updates automatically every second without refreshing the page.

The second feature is a dark mode button. When the button is clicked, JavaScript changes the page styling by toggling a CSS class on the body element.

These features demonstrate scripting because the website is not only static HTML and CSS. JavaScript is used to change the page content and appearance dynamically.

## How to Rebuild This Project

1. Sign in to the AWS Management Console.
2. Open the EC2 service.
3. Launch a new Ubuntu EC2 instance.
4. Create or select a key pair for SSH access.
5. Configure the security group to allow port 22 for SSH and port 80 for HTTP web traffic.
6. Connect to the server using SSH.
7. Run `sudo apt update`.
8. Install Apache using `sudo apt install apache2 -y`.
9. Enable Apache using `sudo systemctl enable apache2`.
10. Start Apache using `sudo systemctl start apache2`.
11. Create the website file named `index.html`.
12. Upload the website file to the server using SCP.
13. Copy the website file into `/var/www/html/index.html`.
14. Restart Apache using `sudo systemctl restart apache2`.
15. Test the website using the public IP address in a browser.

## Testing

The website was tested by opening the public IP address in a web browser:

```text
http://15.135.138.233
```

The JavaScript date and time feature was tested by confirming that the time updates automatically every second.

The dark mode feature was tested by clicking the Toggle Dark Mode button and confirming that the website colours changed.

## Project Reflection

This project helped me understand how cloud infrastructure is used to host websites in a real-world environment. I learned how to launch an EC2 instance, connect to a Linux server using SSH, install and manage Apache, upload website files, and make a website publicly accessible through a cloud server.

The project also helped me understand the difference between using Infrastructure-as-a-Service and using a website builder or Software-as-a-Service platform. With IaaS, I had more control over the server configuration and deployment process.

## References

* Amazon Web Services EC2 documentation
* Apache web server documentation
* GitHub Markdown documentation
* ICT171 lab material
