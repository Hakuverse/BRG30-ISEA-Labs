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

# Lab 1a. Installing VMware and Ubuntu ISO set up. 

I installed VMware Workstation Pro and downloaded the latest ubuntu iso file `ubuntu-26.04-desktop-amd64`. I created a virtual machine on VMware Workstation and allocated 40GB of Hard Disk memory to it, with a split virtual disk into multiple files option selected. I then use the Ubuntu iso file to setup the Linux environment in my VMware Workstation, this includes setting the language, name, etc and a final review at the end before Ubuntu is installed. 
<img width="1540" height="1074" alt="image" src="https://github.com/user-attachments/assets/075f5b20-e054-4e29-b6b1-36a9d976c76e" />
<img width="1186" height="713" alt="image" src="https://github.com/user-attachments/assets/3947a705-5ea4-4c33-81aa-f082a6499ce3" />
<img width="1540" height="1072" alt="image" src="https://github.com/user-attachments/assets/e7ff8d62-ff2f-4325-975a-213e62a110ad" />
<img width="428" height="430" alt="image" src="https://github.com/user-attachments/assets/b2b06d62-3a9c-4429-b5da-534ff11f94e2" />
<img width="428" height="430" alt="image" src="https://github.com/user-attachments/assets/3f8dd521-b4aa-4a46-a15e-4938cd3c147d" />
<img width="1284" height="913" alt="image" src="https://github.com/user-attachments/assets/9fa7942a-ff4b-4d02-a0ef-e4f43ee8fccc" />
<img width="1284" height="913" alt="image" src="https://github.com/user-attachments/assets/69e6a58f-d215-427d-8874-cca6a37d24b8" />
<img width="1284" height="913" alt="image" src="https://github.com/user-attachments/assets/f20f96c6-7d4d-43d7-9f41-40f3c2419a92" />
Once Ubuntu is successfully installed, there will be a message to Restart the system. After that we can navigate to the files available and open our Terminal from there. 
<img width="1284" height="913" alt="image" src="https://github.com/user-attachments/assets/a91fdcb0-f772-4d2f-9402-096593e80206" />
Terminal can be opened and we can move to the next step, checking and installing necessary packages. 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/768aad5c-4955-4e94-aa32-d069211a2f5d" />
With `sudo apt install openssh-server -y` and `sudo systemctl start ssh`, we install the SSH into our system and we check if it's enabled and running by entering `sudo systemctl status ssh`. 
Next, we move on to Ubuntu Desktop and Command Line Familiarisation. 
First I use `firefox &` to open and check the network of FireFox browser. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/8e8de9a7-4c46-42b3-93e6-b08dcc9802c0" />
Next, I tried to open LibreOffice by using `libreoffice --writer &` and it successfully loaded. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/16d05fe9-6bde-425a-8ee1-7e1f5a2c2893" />
Then, I use `nautilus &` to open the files
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/17e5f01a-9237-4f0b-bf77-247a25d1a259" />
Then, I use `sudo snap install gimp` to install the GNU Image Manipulation Program
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/e45f7b16-bfca-4818-bd1c-1193abf45715" />
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/21745b3c-c70c-4654-8b53-bae6f6800658" />
For the next part, `ps -e | head -20` is used to see the information of all running processes on the system currently. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/0d048e96-cebc-4902-8001-692796c23dfb" />
`htop` is also used to view more visual of the process viewer. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/9188cfce-a73a-4056-a6ef-a39ea0d849a2" />
Next, `ls -la` is used to show hidden files like .profile and .bashrc 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/d224b063-8ed2-4c03-9cbb-a899bc8bf294" />
Next, I test the CLI for creating and editing the files, and also to edit the file using nano editior. 
This is directly created and input the message into the testfile.txt
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/b05db849-bfd8-4ebc-ae43-8d81b4477794" />
Now, I try to open the file using Nano editor `nano testfile.txt` 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/e9435de7-9499-4634-a807-ca0630cae9c3" />
Next, I will try to create a test directory structure by using `mkdir -p ~/test/{dir1,dir2}`, and interact with the file operations, deleting empty directory and remove directory with contents, then we check for the disk usage. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/8e3df52b-73e7-4247-84b9-b765601a70ac" />
I then check the kernel info by using `uname -a` and distribution information using `lsb_release -a`, and also the host info using `hostnamectl`.
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/c09d6d12-ebec-441c-bace-4799349a95b4" />
I then check the CPU info by using lscpu and since there is too much stuff, we narrow down by setting conditions `cat /proc/cpuinfo | grep "model name" | head -1`.
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/3a2d3e94-3bf9-42bd-a5bd-c83b2f292001" />
Next I try out the Superuser info, to see the current user, I use `whoami` and the root with `sudo whoami`. I then try to add a user without the sudo command which will trigger an error, and then try to add a user (testuser) with the sudo command that will result in a success, then verify the user with `id testuser`. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/1bbaee46-d986-4129-9917-c97c5857c10c" />
Next, I show my IP adress with `ip a`. I can see the IP is 192.168.91.129 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/fa62cde2-ac7c-4e57-9c69-04f0822e6bd9" />
and I do a ping test on google.com using `ping -c 4 google.com` and see there's sucessful replies. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/c3f6a666-8831-4708-81ac-4b300c234965" />
Next I try to backup original hosts file by using `sudo cp /etc/hosts /etc/hosts.backup`, I then edit the hosts files using `sudo nano /etc/hosts` to add `8.8.8.8 GoogleEpicDNS` as an alias to test the ping using `ping -c 2 GoogleEpicDNS` instead, I also try to test the local mapping using alias mylocal.dev by adding it into my /etc/hosts. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/1e9baa45-031b-4894-8442-29251af6ff8e" />
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/0ddeb48c-95f6-4ff2-8c0c-2f5c9160e2e8" />
Next I do a nslookup on google.com to show the resolved IP address. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/2be24b0b-7be8-4c4c-8416-9908ba6c4b3b" />
Now I move to Public vs Private IP address, I can find our Private IP from earlier using `ip a | grep inet | grep -v inet6` to get 192.168.91.129 and our Public IP via curl using `curl ifconfig.me` , `curl ipinfo.io/ip`, or `curl icanhazip.com` which show us 210.10.77.59. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/e328afb1-9f19-460b-9eb6-006f85da40c8" />
I compare this again using our browser to access https://whatismyipaddress.com, result is shown to be 210.10.77.59 too.
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/08df475d-a9b8-47f8-82f3-9f9ca68ac163" />
Next, I find our hardware information using `lsusb` and `lspci` to see the USB devices and PCI devices like graphics or network. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/ea796d8c-a0f9-4a13-876e-87208f2d5727" />
Next I used Software Installation, SaaS (browser-based) to login to Google Docs using my Firefox web browser. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/f37e640a-91b3-43ae-88cf-f7cce6c761bc" />
Then I tryout the apt usage by updating and upgrading all packages. 
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/f950291a-a889-4834-ae25-cfc8129b9e84" />
Lastly, I did a source code compilation with gcc, checked the file permissions, and ran the program.
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/8dc33a14-a3cc-43e0-9ef7-e6d7c6e544d5" />

# Lab 1a reflection. 

At first, when i first downloaed a virtual machine, i picked VirtualBox to setup my linux environment, but VirtualBox keeps giving me errors while setting up, it takes at least 30mins of loading and ended up giving me an Error message. I have to resolve this issue by changing to a different virtual machine, VMware Workstation, and it ran perfectly.
Virtual machines has a few key advantage for testing and development, first is isolation, VM runs completely in a separate environment from the host OS. If the VM crash or gets infected with malware, the host will not get affected at all. This is good for testing unstable softwares or security tools. Secondly, VM is Cost effective, Instead of getting multiple physical servers, you can run multiple VMs on one host, this costs much lesser than getting multiple physical servers. Thirdly, you can export a VM and share it with working colleagues so everyone can get the same environment and settings, eliminating the unncessary non working conditions for different machines.
At first I only allocate 1GB of RAM to the VM and it made Ubuntu very slow and unresponsive, then i changed back to 4096 MB, and it solved the issue.
Before this lab, I thought Linux was just one operating system, but now i learned that Linux is actually just the kernel, the core that manages the hardware, processes, and memory. Different distribution package the kernel with different software, package managers, desktop environments, and configuration to do different things. Ubtuntu was an good choice because it is beginner friendly, and widely used in cloud environments such as AWS and Azure. 

============================================================================================

# Lab 1b. Linux Servies, Permissions, and File System Search 

First I install the Apache Web Server using `sudo apt install apache2 -y` and test it using firefox browser with `http://127.0.0.1` 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/54b500da-32cc-41c9-b510-bc1781a07f90" />
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/d7c673f4-f653-46ad-9e70-43f8d8f6dcf7" />
Next I replace the content with my own text using `sudo nano /var/www/html/index.html` 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/9a07dacc-828e-4d88-92b7-ae660749ca37" />
Now I run a health check for my apache web server using `sudo systemctl status apache2` and firefall rules using `sudo ufw status verbose`
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/cc0c04ab-f9d4-42dd-81ec-fa1514bcba6b" />
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/62db66ca-0ebe-47be-9027-73a739dd88d2" />
Now I create 3 users, alice, bob and mallory, a projectgroup group and add only alice and bob to the group, I will create a shared folder, and test alice (success) and mallory (fail) 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/014c3e5a-84d7-4dad-8262-cb81a60557a4" />
with `ls -ld /home/shared` showing `drwxrwx---`, the directory /home/shared can only be accessed by the owner and members of the group assigned to it.
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/3dd28def-e9fe-4c6f-8809-236695f132cf" />
Next I procees to do a file search using find and grep. I used `find /etc -name "*.conf" | head -10` to find all .conf files in /etc
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/7ef47102-8ba0-4b8c-afce-22ece6cd2a51" />
and `grep -r "error" /var/log/ 2>/dev/null | head -5` to search inside files.
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/55e0ac4e-bbe8-4ab8-a4ca-fefc84ae3535" />














