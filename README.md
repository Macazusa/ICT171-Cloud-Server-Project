# ICT171 Cloud Server Project

## Student Details

Name: Aidan Macliver
Student Number: 33401722
Unit: ICT171 Introduction to Server Environments and Architectures
Project: Cloud-hosted personal portfolio website

## Project Links

Website URL: http://15.135.138.233
Public IP Address: 15.135.138.233
GitHub Repository: https://github.com/Macazusa/ICT171-Cloud-Server-Project
Video Explainer: [Paste video link here]
DNS Entry: Not configured at time of submission

## Project Overview

This project involved creating a cloud-hosted personal portfolio website using Infrastructure-as-a-Service. I used Amazon EC2 to deploy a Linux virtual server and installed Apache to host the website. The website is accessible online through a public IP address.

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
| 6 June 2026   | GitHub documentation was completed.                                               |

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

* A project overview section
* A cloud infrastructure section
* A server setup section
* A scripting section
* A testing and verification section
* Student details
* Live JavaScript date and time display
* Dark mode button
* Interactive tab navigation

The website is hosted on the EC2 instance and can be accessed using the public IP address.

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

http://15.135.138.233

The script output can be tested by:

1. Watching the date and time update automatically at the top of the page.
2. Clicking the Toggle Dark Mode button and confirming the website changes colour.
3. Clicking the navigation tabs and confirming that different sections appear without loading a new page.

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

The tab navigation feature was tested by clicking each navigation tab and confirming that the correct content section was displayed.

## DNS and SSL/TLS

At the time of submission, the website was accessible through the EC2 public IP address. A custom DNS entry and full HTTPS configuration were not completed before submission.

Port 443 was opened in the AWS security group for future HTTPS configuration. In a future improvement, a custom domain could be connected using a DNS A record pointing to the EC2 public IP address, and HTTPS could be configured using Let's Encrypt Certbot.

## Use of External Assistance and AI Tools

This project used AI assistance to help structure the HTML, CSS, JavaScript and documentation. The code was adapted for my ICT171 personal portfolio website and tested on my own Amazon EC2 server.

The server deployment was completed by me. I launched the EC2 instance, connected using SSH, installed Apache, uploaded the website file, copied it into `/var/www/html/index.html`, restarted Apache, and tested the website using the public IP address.

The JavaScript features used in this project are:

* A live date and time display that updates every second.
* A dark mode button that changes the page appearance by toggling a CSS class.
* Interactive tab navigation that shows and hides website sections.

These features were included to meet the scripting component of the assignment. The output can be verified online at:

http://15.135.138.233

## Project Reflection

This project helped me understand how cloud infrastructure is used to host websites in a real-world environment. I learned how to launch an EC2 instance, connect to a Linux server using SSH, install and manage Apache, upload website files, and make a website publicly accessible through a cloud server.

The project also helped me understand the difference between using Infrastructure-as-a-Service and using a website builder or Software-as-a-Service platform. With IaaS, I had more control over the server configuration and deployment process.

The scripting component helped me understand how JavaScript can be used to make a website more interactive. The live clock, dark mode button and tab navigation all provide visible outputs that can be tested directly on the website.

## References

* Amazon Web Services EC2 documentation
* Apache web server documentation
* GitHub Markdown documentation
* ICT171 lab material
* ChatGPT assistance for structuring HTML, CSS, JavaScript and documentation
