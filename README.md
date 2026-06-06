# ICT171 Cloud Server Project

## Student Details

Name: Aidan Macliver
Student Number: 33401722
Unit: ICT171 Introduction to Server Environments and Architectures
Project: Cloud-hosted personal portfolio website

## Project Links

Website URL: https://aidanmacliver.com
Alternative URL: https://www.aidanmacliver.com
Elastic IP Address: 3.105.182.179
DNS Entry: aidanmacliver.com
GitHub Repository: https://github.com/Macazusa/ICT171-Cloud-Server-Project
Video Explainer: [Paste video link here]

## Project Overview

This project involved creating a cloud-hosted personal portfolio website using Infrastructure-as-a-Service. I used Amazon EC2 to deploy a Linux virtual server and installed Apache to host the website. The website is accessible online through a custom domain name and is secured using HTTPS.

The purpose of this project was to demonstrate how a website can be deployed, configured and managed on a cloud server rather than using local hosting or a Software-as-a-Service website builder.

The website includes multiple interactive JavaScript features, including a live date and time display, a dark mode toggle, and tab-style navigation that shows and hides different sections of the website.

## Development Timeline

| Date          | Activity                                                                          |
| ------------- | --------------------------------------------------------------------------------- |
| 22 April 2026 | Initial AWS EC2 server was created during the early project stage.                |
| 6 June 2026   | Final Ubuntu EC2 instance was launched for the submitted portfolio website.       |
| 6 June 2026   | Apache was installed and configured.                                              |
| 6 June 2026   | Website files were created and uploaded to the server.                            |
| 6 June 2026   | JavaScript date/time and dark mode features were added.                           |
| 6 June 2026   | Interactive JavaScript tab navigation was added to improve website functionality. |
| 6 June 2026   | An Elastic IP address was associated with the EC2 instance.                       |
| 6 June 2026   | Cloudflare DNS A records were configured for the custom domain.                   |
| 6 June 2026   | HTTPS was configured using Certbot and Let's Encrypt.                             |
| 6 June 2026   | GitHub documentation was updated with DNS and SSL/TLS configuration details.      |

## Cloud Provider

Cloud provider: Amazon Web Services
Service used: Amazon EC2
Operating system: Ubuntu Linux
Web server: Apache
DNS provider: Cloudflare
SSL/TLS certificate provider: Let's Encrypt

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

## Elastic IP Configuration

An Elastic IP address was associated with the EC2 instance so the server would have a stable public IP address for DNS configuration.

Elastic IP address:

```text
3.105.182.179
```

This IP address was then used in Cloudflare DNS records to point the domain name to the EC2 server.

## Security Group Configuration

The following inbound ports were configured:

| Port | Purpose           |
| ---- | ----------------- |
| 22   | SSH access        |
| 80   | HTTP web traffic  |
| 443  | HTTPS web traffic |

SSH was used for remote server administration. HTTP was used for normal web traffic and for Let's Encrypt certificate validation. HTTPS was configured after the domain name was connected to the server.

## Website Deployment

The website was created using HTML, CSS and JavaScript. The completed `index.html` file was uploaded to the server using SCP and copied into the Apache web root directory.

Commands used:

```bash
scp -i "ICT171-aidan-key.pem" index.html ubuntu@3.105.182.179:/home/ubuntu/index.html
sudo cp /home/ubuntu/index.html /var/www/html/index.html
sudo systemctl restart apache2
```

The Apache web root directory used for this project was:

```bash
/var/www/html/
```

## DNS Configuration

A custom domain name was configured for this project using Cloudflare DNS. The domain was connected to the Amazon EC2 server using DNS A records.

| Record Type | Name | Value         | Proxy Status |
| ----------- | ---- | ------------- | ------------ |
| A           | @    | 3.105.182.179 | DNS only     |
| A           | www  | 3.105.182.179 | DNS only     |

The domain was tested by opening the website in a browser:

```text
http://aidanmacliver.com
http://www.aidanmacliver.com
```

After confirming that the domain pointed to the EC2 server, HTTPS was configured.

## SSL/TLS Configuration

HTTPS was configured using Let's Encrypt Certbot with Apache.

Commands used:

```bash
sudo apt update
sudo apt install certbot python3-certbot-apache -y
sudo certbot --apache -d aidanmacliver.com -d www.aidanmacliver.com
```

Certbot successfully issued and deployed a certificate for:

```text
aidanmacliver.com
www.aidanmacliver.com
```

The certificate files were saved on the server at:

```text
/etc/letsencrypt/live/aidanmacliver.com/fullchain.pem
/etc/letsencrypt/live/aidanmacliver.com/privkey.pem
```

The website was tested successfully using HTTPS:

```text
https://aidanmacliver.com
https://www.aidanmacliver.com
```

## Website Functionality

The website is a personal portfolio page that includes:

* A project overview section
* A cloud infrastructure section
* A server setup section
* A scripting section
* A testing and verification section
* Student details
* Live JavaScript date and time display
* Dark mode button
* Interactive tab navigation
* HTTPS access through a custom domain name

The website is hosted on the EC2 instance and can be accessed using the custom domain name.

## Scripting Component

The website includes JavaScript scripting features.

### Feature 1: Live Date and Time

The first JavaScript feature dynamically displays the current date and time at the top of the website. The time updates automatically every second without needing to refresh the page.

### Feature 2: Dark Mode Toggle

The second JavaScript feature is a dark mode button. When the button is clicked, JavaScript toggles a CSS class on the page body. This changes the website between the normal light theme and a dark theme.

### Feature 3: Interactive Tab Navigation

The third JavaScript feature is interactive tab navigation. When a navigation tab is clicked, JavaScript hides the other website sections and displays the selected section. This makes the website more interactive than a basic static page and allows users to move between sections more clearly.

These scripting features demonstrate that the website is not only static HTML and CSS. JavaScript is used to change the page content and appearance dynamically.

## Script Code Explanation

The live date and time feature uses the JavaScript `Date()` object to get the current date and time. The `setInterval()` function runs the update every second.

The dark mode feature uses `classList.toggle()` to add or remove the `dark-mode` CSS class from the page body.

The tab navigation feature uses `querySelectorAll()` to find all tab sections and buttons. It then removes the active classes from all sections and buttons before applying the active class to the selected tab and section.

## Script Verifiable Output

The output of the JavaScript can be verified directly on the live website:

```text
https://aidanmacliver.com
```

The script output can be tested by:

1. Watching the date and time update automatically at the top of the page.
2. Clicking the Toggle Dark Mode button and confirming the website changes colour.
3. Clicking the navigation tabs and confirming that different sections appear without loading a new page.

## How to Rebuild This Project

1. Sign in to the AWS Management Console.
2. Open the EC2 service.
3. Launch a new Ubuntu EC2 instance.
4. Create or select a key pair for SSH access.
5. Configure the security group to allow ports 22, 80 and 443.
6. Connect to the server using SSH.
7. Run `sudo apt update`.
8. Install Apache using `sudo apt install apache2 -y`.
9. Enable Apache using `sudo systemctl enable apache2`.
10. Start Apache using `sudo systemctl start apache2`.
11. Create the website file named `index.html`.
12. Upload the website file to the server using SCP.
13. Copy the website file into `/var/www/html/index.html`.
14. Restart Apache using `sudo systemctl restart apache2`.
15. Allocate an Elastic IP address in AWS.
16. Associate the Elastic IP address with the EC2 instance.
17. Create DNS A records in Cloudflare pointing `@` and `www` to the Elastic IP address.
18. Test the domain using HTTP.
19. Install Certbot using `sudo apt install certbot python3-certbot-apache -y`.
20. Run Certbot using `sudo certbot --apache -d aidanmacliver.com -d www.aidanmacliver.com`.
21. Test the website using HTTPS.

## Testing

The website was tested by opening the custom domain name in a web browser:

```text
https://aidanmacliver.com
```

The `www` version was also tested:

```text
https://www.aidanmacliver.com
```

The JavaScript date and time feature was tested by confirming that the time updates automatically every second.

The dark mode feature was tested by clicking the Toggle Dark Mode button and confirming that the website colours changed.

The tab navigation feature was tested by clicking each navigation tab and confirming that the correct content section was displayed.

HTTPS was tested by confirming that the website loaded using `https://` without a browser certificate warning.

## Use of External Assistance and AI Tools

This project used AI assistance to help structure the HTML, CSS, JavaScript and documentation. The code was adapted for my ICT171 personal portfolio website and tested on my own Amazon EC2 server.

The server deployment was completed by me. I launched the EC2 instance, connected using SSH, installed Apache, uploaded the website file, copied it into `/var/www/html/index.html`, restarted Apache, configured an Elastic IP address, connected the domain using Cloudflare DNS, configured HTTPS using Certbot, and tested the website using the custom domain name.

The JavaScript features used in this project are:

* A live date and time display that updates every second.
* A dark mode button that changes the page appearance by toggling a CSS class.
* Interactive tab navigation that shows and hides website sections.

These features were included to meet the scripting component of the assignment. The output can be verified online at:

```text
https://aidanmacliver.com
```

## Project Reflection

This project gave me a basic understanding on cloud infrastructure and how it is used to host websites in a real environment. I learned how to launch an EC2 instance, connect to a linus server using SSH, install and manage Apache, upload website files, and make a website publicly accessible through a cloud server.

I also learned how Elastic IP Addresses can keep a consistent public IP address for DNS records. I chose Cloudlfare to manae the DNS records for the custom domain, and Certbot with Lets Encrypt was used to configure HTTPS for apache

This project gave me a greater understanding on the difference between using Infrastructure as a Service and using a web builder or Software as a service platform. With Iaas, I could control server configuration, DNS setup and HTTPS configuration.

The scripting component gave me a better perspective on how JavaScript can be used to make websites interactive. The live time, dakr mode button and tab navigation provode outputs that can be tested on the website.

## References

* Amazon Web Services EC2 documentation
* Apache web server documentation
* Cloudflare DNS documentation
* Let's Encrypt documentation
* Certbot documentation
* GitHub Markdown documentation
* ICT171 lab material
* ChatGPT assistance for structuring HTML, CSS, JavaScript and documentation
