# BRG30-ISEA-Labs
ICT171 Introduction to Server Environments and Architectures BRG-30
Student ID : CT0390892 
========================================================================
# Introduction

This reflective journal documents my hands-on learning journey through a series of practical lab activities in Linux system administration, cloud deployment, networking, security, automation, and cotainerisation. The obejctive was to move beyond the theory knowledge and gain real-world skills that are directly applicable to jobs such as system admin, DevOps engineer, or cloud consultant.
Over the course of the bridging module, i worked through a comprehensive set of tasks organised into 4 lab activities.


Lab 1 - Linux Environment & System-Level Commands

Setting up Ubuntu on VMware Workstation, learning essential command-line tools, file operations, user privilege management, network configurationm and software installations.

Lab 2 - Services, Permissions, Cloud, and TCO 

Configuring Apache2 and SSH, implementing firewall rules (UFW), managing Linux permissions and group access, performing a Total Cost of Ownership (TCO) analysis for printers, and deploying my first cloud virtual machine on AWS EC2. 

Lab 3 - DNS, SSL & Domain Management 

Registering a free dynamic DNS domain with DuckDNS, linking it to my EC2 instance, and securing the web server with a Let's Encrypt TLS certificate using Certbot, enabling full HTTPs with automatic renewal. 

Lab 4 - Automation, Scripting and Additional Service 

Writing a Bash backup script with timestamped archives, scheduling it with cron, and deploying a Docker container (Nginx) as an additional server service, showing mordern, repeatable deployment practices in real life situations. 

Throughout each activity, I encountered and solved real problems. From debugging Apache configuration and fixing security group rules, to troubleshooting DNS propagation and certbot challenges. These experiences reinforced the importance of systematic troubleshooting, documentation, and the value of infrastructure as code. 

All work mentioned above is documented with screenshots, command outputs, and scripts below. This journal also includes the link to a video walkthrough that shows every lab component in action, along with personal reflections on the 'why' behind each decision. 

============================================================================================

Lab 1a. Installing VMware and Ubuntu ISO set up. 

I installed VMware Workstation Pro and downloaded the latest ubuntu iso file `ubuntu-26.04-desktop-amd64`. I created a virtual machine on VMware Workstation and allocated 40GB of Hard Disk memory to it, with a split virtual disk into multiple files option selected. I then use the Ubuntu iso file to setup the Linux environment in my VMware Workstation, this includes setting the language, name, etc and a final review at the end before Ubuntu is installed. 
<img width="1540" height="1074" alt="image" src="https://github.com/user-attachments/assets/075f5b20-e054-4e29-b6b1-36a9d976c76e" />
<img width="1186" height="713" alt="image" src="https://github.com/user-attachments/assets/3947a705-5ea4-4c33-81aa-f082a6499ce3" />
<img width="1540" height="1072" alt="image" src="https://github.com/user-attachments/assets/e7ff8d62-ff2f-4325-975a-213e62a110ad" />
<img width="428" height="430" alt="image" src="https://github.com/user-attachments/assets/b2b06d62-3a9c-4429-b5da-534ff11f94e2" />
<img width="428" height="430" alt="image" src="https://github.com/user-attachments/assets/3f8dd521-b4aa-4a46-a15e-4938cd3c147d" />
<img width="1284" height="913" alt="image" src="https://github.com/user-attachments/assets/9fa7942a-ff4b-4d02-a0ef-e4f43ee8fccc" />
<img width="1284" height="913" alt="image" src="https://github.com/user-attachments/assets/69e6a58f-d215-427d-8874-cca6a37d24b8" />
<img width="1284" height="913" alt="image" src="https://github.com/user-attachments/assets/f20f96c6-7d4d-43d7-9f41-40f3c2419a92" />
Once Ubuntu is successfully installed, there will be a message to Restart the system. 
