# BRG30-ISEA-Labs
ICT171 Introduction to Server Environments and Architectures BRG-30
Student ID : CT0390892 
========================================================================
# Introduction

This reflective journal documents my hands-on learning journey through a series of practical lab activities in Linux system administration, cloud deployment, networking, security, automation, and containerisation using Docker. The objective was to move beyond the theory knowledge and gain real-world skills that are directly applicable to jobs such as system admin, DevOps engineer, or cloud consultant.
Over the course of the bridging module, I worked through a comprehensive set of tasks organised into 4 major lab activities.


Lab 1 - Linux Environment & System-Level Commands

Setting up Ubuntu on VMware Workstation, learning essential command-line tools, file operations, user privilege management, network configuration and software installations.

Lab 2 - Services, Permissions, Cloud, and TCO 

Configuring Apache2 and SSH, implementing firewall rules (UFW), managing Linux permissions and group access, performing a Total Cost of Ownership (TCO) analysis for printers, and deploying my first cloud virtual machine on AWS EC2. 

Lab 3 - DNS, SSL & Domain Management, Automation and Scripting 

Registering a free dynamic DNS domain with DuckDNS, linking it to my EC2 instance, and securing the web server with a Let's Encrypt TLS certificate using Certbot, enabling full HTTPs with automatic renewal. 

Writing a Bash backup script with timestamped archives, scheduling it with cron, 

Lab 4 - Additional Server Service 

Deploying a Docker container (Nginx) as an additional server service, showing mordern, repeatable deployment practices in real life situations. 

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

At first, when I first downloaed a virtual machine, I picked VirtualBox to setup my linux environment, but VirtualBox keeps giving me errors while setting up, it takes at least 30mins of loading and ended up giving me an Error message. I have to resolve this issue by changing to a different virtual machine, VMware Workstation, and it ran perfectly.

Virtual machines has a few key advantage for testing and development, first is isolation, VM runs completely in a separate environment from the host OS. If the VM crash or gets infected with malware, the host will not get affected at all. This is good for testing unstable softwares or security tools. Secondly, VM is Cost effective, Instead of getting multiple physical servers, you can run multiple VMs on one host, this costs much lesser than getting multiple physical servers. Thirdly, you can export a VM and share it with working colleagues so everyone can get the same environment and settings, eliminating the unncessary non working conditions for different machines.
At first I only allocate 1GB of RAM to the VM and it made Ubuntu very slow and unresponsive, then I changed back to 4096 MB, and it solved the issue.

I install because `openssh-server` SSH allows secure remote access to the server without physical access, which is the standard in cloud and enterprise environments, similarily using `ufw` (Uncomplicated Firewall) provides a simplified interface to iptables, letting me define which ports are exposed and reducing the attack surface.

Before this lab, I thought Linux was just one operating system, but now I learned that Linux is actually just the kernel, the core that manages the hardware, processes, and memory. Different distribution package the kernel with different software, package managers, desktop environments, and configuration to do different things. Ubtuntu was an good choice because it is beginner friendly, and widely used in cloud environments such as AWS and Azure. 

============================================================================================

# Lab 1b. Linux Servies, Permissions, and File System Search 

First I install the Apache Web Server using `sudo apt install apache2 -y` and test it using firefox browser with `http://127.0.0.1` 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/54b500da-32cc-41c9-b510-bc1781a07f90" />
<img width="1622" height="1077" alt="image" src="https://github.com/user-attachments/assets/d7c673f4-f653-46ad-9e70-43f8d8f6dcf7" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/955e9537-5bdb-4cdf-9fbf-e5948a984c1d" />

Next I replace the content with my own text using `sudo nano /var/www/html/index.html` 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/9a07dacc-828e-4d88-92b7-ae660749ca37" />
Now I run a health check for my apache web server using `sudo systemctl status apache2` and firefall rules using `sudo ufw status verbose`
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/cc0c04ab-f9d4-42dd-81ec-fa1514bcba6b" />
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/62db66ca-0ebe-47be-9027-73a739dd88d2" />
Now I check the listening ports to confirm Apache is on 80 and SSH is on 22 using `sudo ss -tulpn | grep -E ':(22|80|443)'` to filter out 22, 80 and 443.
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/b4fa6c61-5f47-481d-9223-8d04d7d5dc9d" />
Find my ip address to share with my powershell to test port 80 using `ip a` we get 192.168.91.129 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/ed06f1cc-c0f1-47e5-9a1f-a01a304a90d0" />
On my windows powershell key in `ipconfig` to find my IPv4 address. 
<img width="1115" height="628" alt="image" src="https://github.com/user-attachments/assets/d436cd9d-4f57-4e6a-b5bf-6655bed2ff1b" />
Install nmap in my VM 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/6e880a9e-6052-4a22-8a57-a4afadc3ac60" />
Now, I can scan my windows host from VM using `nmap (ipaddress)` 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/552e040b-f0bc-402d-a86f-fadb8c8c699c" />
now I open apache from my VM and scan my VM's ip using windows. 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/54cb421f-46b5-47c6-adcd-24de7eef03b4" />
Notice that Nmap output showing port 80 as open.
<img width="1115" height="628" alt="image" src="https://github.com/user-attachments/assets/39c5e469-dce3-40b1-8085-38306385e419" />
Now I remove apache on my VM and scan again on my Windows Powershell. 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/00b8b0eb-581b-4442-9321-0631f9cd6d06" />
Notice that Nmap output now showing port 80 closed. 
<img width="1115" height="628" alt="image" src="https://github.com/user-attachments/assets/7c70bf76-281c-48e7-aeda-0d9d62cfed14" />
Next, I will create 3 users, alice, bob and mallory
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/433b375e-d336-432e-8e86-4f0867c46fc9" />
I will create a group called project group and add only alice and bob to the group, and check the groups they have.
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/66caff38-ca25-4aa5-967c-c6a4c3d0302d" />
I will now create a shared directory with 10 files, and set the ownership and permissions. 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/f34c5ef1-d3d7-4679-b02f-975919eb34a9" />
Now I will do a test access for alice as well as mallory, (alice should success and mallory should fail). 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/296f0f72-e4e0-4b88-87e0-5fe206138184" />
Now I will orverride bob's rights to write 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/8358b474-c242-4c57-a041-099869ff971f" />
Next, I will open the extracter fold gutenberg and find all .txt files. 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/7a06d7b5-09a8-4102-9503-53795355fc69" />
Now, I will use grep to search for the word 'disaster' 
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/8622951a-5852-4bb1-9f02-1ff7c72bba78" />
Next I procees to do a file search using find and grep. I used `find /etc -name "*.conf" | head -10` to find all .conf files in /etc
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/7ef47102-8ba0-4b8c-afce-22ece6cd2a51" />
and `grep -r "error" /var/log/ 2>/dev/null | head -5` to search inside files.
<img width="1546" height="1077" alt="image" src="https://github.com/user-attachments/assets/55e0ac4e-bbe8-4ab8-a4ca-fefc84ae3535" />

# Lab 1b reflection. 

Lab 1b showed me how making Linux behave like a real server, I started by installing Apache and SSH, then securing using UFW, this taught me that running a service is easy but securing it requires deliberate firewall rules. Using nmap my VM's ports before and after removing Apache also showed me how visible every service is on a network. The permissions lab was also very eye opening. I created 3 users (alice, bob and mallory) and a shared group, then set `chmod 770` on `/home/shared`. Testing their access by switching users proved that when a user that is not in the group truly has no access. I now understand why `chmod777` is dangerous. Finally, the file search with Gutenberg archive teach me the power of the command line tools. find, grep helped me locate and find the files and texts when I needed them. Overall, lab 1b gave me confidence in securing services, managing permissions, and navigating large file systems, which is an essential skill required for any system admins. 

============================================================================================

# Lab 2a. TCO Analysis (Printer Comparison) 

TCO means Total Cost of Ownership, which is a comprehensive financial estimate that evaluates the true, lifetime cost of an asset or service, it includes the direct expenses, the operating costs, the maintenance fee, and the hidden fees over the asset's lifespan. 

I will be comparing two different type of Printers, an entry-level home inkjet printer vs an Entry-level small office monochrome laser. 
The Inkjet printer I have chosen the Epson EcoTank ET-2850, and the Laser printer I have chosen the Brother HL-L2350DW.
For the Inkjet printer, its for personal / shared family use, the print speed is 10.5ppm for monochrome and 5ppm for colored, it consumes a refillable ink bottles with black inks at $24.99/bottle and colored inks at $16.99/bottle, the printer is priced at $349.99. 
<img width="1114" height="459" alt="image" src="https://github.com/user-attachments/assets/1f021a8e-da7f-426f-a383-0f7bedd0934d" />
<img width="1238" height="624" alt="image" src="https://github.com/user-attachments/assets/7c5261c3-482f-4534-9c41-46b52f556e19" />
For the Laser printer, it's for workgroup / office use, the print speed is 32ppm and it consumes a toner cartridge and a drum at $98.29 and $129.49 respectively, the printer is priced at $119.99.
<img width="1045" height="474" alt="image" src="https://github.com/user-attachments/assets/d8104b42-3a9f-4123-b764-442eaa9924bf" />
<img width="849" height="167" alt="image" src="https://github.com/user-attachments/assets/87e971cb-38e1-4cc4-ac91-fd55d6e31d29" />
<img width="834" height="153" alt="image" src="https://github.com/user-attachments/assets/72a7f6f8-8078-4612-8522-a71fee0be2e1" />

Assumptions 
1. Time period = 5 years
2. Pages per week = 750
3. Total pages over 5 years = 195,000 pages
4. Electricity cost = $0.30 per kWh
5. Runtime per week = 40 hours
6. Total hours over 5 years = 10,400 hours
7. Paper cost (500 sheets) = $6.00 per ream
8. Total Paper reams 390
9. Colour mix assumption for inkjet = 70% black and white, 30% color
10. Colour mix assumption for laser = 100% black and white
11. Drum Unit for Laser = 12,000 pages/drum 
12. Power consumption - inkjet (printing) = 15W
13. Power consumption - inkjet (standby) = 1.7W
14. Power consumption - laser (printing) = 460W
15. Power consumption - laser (standby) = 48W

List of Expense Items 

1. Epson EcoTank ET-2850 Inkjet printer
   
   I.Printer Unit - one time purchase
   
   ii. Black Ink Bottle - Refill bottles, ~7500 pages each
   
   iii. Colour Ink Bottles - 3 separate bottles per set, ~6000 pages each
   
   iv. Paper (reams of 500) - standard 80gsm copy paper, $6/ream
   
   v. Electricity - 15W printing, 1.7W standby @ $0.30/kWh
   
2. Brother HL-L2350DW Laser printer
   
   I. Printer Unit - one time purchase 

   ii. High-Yield Toner Cartridge - 3000 pages/cartridge

   iii. Drum Unit - 12,000 pages/drum

   iv. Paper (reams of 500) - standard 80gsm copy paper, $6/ream

   v. Electricity - 460W printing, 48W standby @ $0.30/kWh


TCO Calculations 

Epson EcoTank ET-2850 Inkjet Printer 

<img width="645" height="251" alt="image" src="https://github.com/user-attachments/assets/13b38284-18a5-4f97-a2b4-b2396e57142c" />

Brother HL-L2350DW Laser Printer

<img width="647" height="258" alt="image" src="https://github.com/user-attachments/assets/2aa51222-8004-4258-8d85-5a107eb3ed8a" />

Cost Per Page 

Inkjet - $3,681.42 / 195,000 = $0.019/page (rounded)

Laser - $11,212.48 / 195,000 = $0.058/page (rounded)

# Lab 2a reflection. 
The Brother HL-L2350DW Laser printer has a 5-year TCO of $11,212.48 versus $3,681.42 for the Epson EcoTank ET-2850 Inkjet printer. On a per page basis, the laser printer comes in at $0.058/page compared to $0.019/page for the inkject. Based on the calculated TCO, the Epson EcoTank ET-2850 jetink printer is the more cost effective printer over 5 years at 750pages per week. Its 5 year TCO is approximately 67% lower than the laser printer.

At 5 pages per week for a home user printing, the inkjet printer comes with enough ink in the box to cover all 1,300 pages, meaning the TCO is approximately $356. The laser printer at $119 would only use 1 toner cartridge and 1 drum, making its TCO around $348. The laser printer still wins on TCO. 

Other qualitative factors that could influence the selection includes, Print quality, the inkjet printer produces color output while the laser printer is monochrome only. Print Speed, the laser is at 32ppm which is 3x more faster than the inkjet at around 10ppm, which matters in a busy office environment. Noise, laser printers tends to be louder during printing than inkjets. 

For a large workgroup printer, I would prioritise a few points, High monthly duty cycle to handle heavy workloads without wear, High yield tonner options to minimise per page costs and reduce the changing frequency, Network connectivity for shared multiple users, Large paper capacity trays to reduce the need to refill frequently, Energy efficiency rating to save electricity and the Total cost of ownership per page. 


============================================================================================

# Lab 2b. Cloud Computing, Bash Scripting & System Automation 


In lab 2b, I will be launching and configuring a Linux VM instance using AWS's Amazon EC2, install Apache, serve web content, and learn cloud deployment basics. Very important thing to note is that in cloud computing, forgetting to stop a VM is a huge mistake with financial consequences. 
<img width="1629" height="830" alt="image" src="https://github.com/user-attachments/assets/12436f88-4d3c-4e8e-9ed3-5591e5921acd" />

First, I navigate to the Security Group tab to create a new security group called 'ssh-and-web' to allow both SSH and HTTP traffic. 
<img width="1636" height="773" alt="image" src="https://github.com/user-attachments/assets/7265a655-7afc-4c47-9e76-bae6d0e1bdeb" />
<img width="1420" height="578" alt="image" src="https://github.com/user-attachments/assets/0a97e654-c92a-4c8b-8408-358865e55d9f" />

Next, I create a new instance in the Amazon EC2, Name it, select Ubuntu 26.04 server, and name the keypair as Hakuverse. 
<img width="1093" height="869" alt="image" src="https://github.com/user-attachments/assets/a39d854c-7f94-4c8f-bb8d-88cb18605f5f" />

Then select the security group we have created previously 'ssh-and-web' 
<img width="1079" height="685" alt="image" src="https://github.com/user-attachments/assets/64ff8c9c-c356-4eb3-84f9-8888225c4c1e" />

Then I launch my instance and from pending state it went to running state. 
<img width="1388" height="671" alt="image" src="https://github.com/user-attachments/assets/0cc2d30e-25b1-4332-8e48-cd1134bbd6f8" />

Now I can use my VMware to connecto to the Ubtuntu VM on EC2, on my VM terminal, I first set the correct permissions `chmod 400 Hakuverse.pem` then I connect by using `ssh -I Hakuverse.pem ubuntu@13.211.234.226` 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/66d60906-b488-4a02-bc8c-621249a916b6" />

After connected to my web server, I update the system by using `sudo apt update` and `sudo apt upgrade -y` then I install Apache Web Server by running `sudo apt install apache2 -y` 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/5b6933fb-109d-4770-b89c-e39e2dd7c86d" />

And I start and enable Apache using `sudo systemctl start apache2` and `sudo systemctl enable apache2` and check the status of Apache by using `sudo systemctl status apache2`. 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/d682df8a-50b9-4d67-baee-6a53b71546f0" />

From here I configure the UFW Firewall. 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/c350d933-a60a-4abb-b740-2aad4b9be580" />

Now I test the Apache Default page by getting the Public IPv4 address from my EC2 console. 
<img width="1389" height="186" alt="image" src="https://github.com/user-attachments/assets/111b024a-d80d-4113-b7c3-f0cd7890e034" />

Open the browser and enter http://13.211.234.226, I should land on the Apache default page, this confirms that EC2 VM is running, Apache is installed and the security group allows HTTP. 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/37d1add8-d1c0-4a44-aade-c13c2f1737d4" />

Now I will try to create custom HTML page by editing the default page using `sudo nano /var/www/html/index.html`. I changed the name to 'My AWB Ubuntu Server' and the button now shows my CT student number. 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/d99baf52-96ff-4a55-89d0-233e8d4b2968" />

Next I will download external file with wget, I have choosen a dummy file from www.w3.org. Now I will verify the downloaded file with `ls -lh ~/` 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/24dbb399-8788-419d-af54-2422f13bae24" />

Now I will copy the file to apache web directory and verify if the file is in the Web Root. 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/5a41116d-2083-4070-a8d9-d67fd2d6ff46" />

Now I will test the PDF accessibility by going to the browser and type in the pdf name after my ip address.
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/51c2b442-7da0-4b13-8706-f0a6cfa1a463" />

I will add a hyperlink to the PDF in the HTML page now by editing in the index.html. 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/10afa175-16e3-4616-9f68-1f3052422928" />

And with that, I have a hyperlink in my HTML page and I can click it to download the PDF
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/238b877f-bd76-403c-9e36-20bc77811dcf" />
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/2a2c71aa-cf88-46bc-a820-cb91b996113a" />

From the AWS EC2, I can check the usage and cost of my server instance by searching Billing and Cost Management in the searchbar. 
<img width="930" height="389" alt="image" src="https://github.com/user-attachments/assets/5de974c7-9e35-4cdd-8462-69c5bbf8f991" />

And from here, I can set my budget alert, cost monitor, I can also check what is the breakdown of the cost usage directly from the AWS console. 
<img width="1630" height="1202" alt="image" src="https://github.com/user-attachments/assets/c5e851db-ce5f-4836-a9c8-51da1aeb07f3" />
<img width="1655" height="1201" alt="image" src="https://github.com/user-attachments/assets/0a0507b0-cd4d-4e8c-b4f0-244148e44fce" />
<img width="1354" height="583" alt="image" src="https://github.com/user-attachments/assets/1f85c784-fa58-45a7-8067-0383010208b2" />

Very important again that Instance must be stopped to prevent money loss. 
<img width="1013" height="175" alt="image" src="https://github.com/user-attachments/assets/308f3b50-84ef-4cf0-beb2-be8ad7fa776c" />

Next, I will move on to the next exercise, Bash Scripting & System Automation. I will first create a working directory, then create files using different methods like `touch`, `echo`, and `cat`. then I will view the file contents without the GUI by using `cat`, `less`, `head`, and `tail`. 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/9459629e-a1d6-420e-a378-1bd15b2faa19" />
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/a61b01f6-fb1f-47a2-96ee-63d107a6fe44" />
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/57ab9ebc-0ae9-4bdd-944e-72ac3b5eb26b" />
Using head shows the first 10 lines by default and using tail shows the last 10 lines. 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/18302ca6-ac30-464f-9000-63be63d71e4e" />

Now I will copy, move, rename, and delete files. 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/1a96a4a1-9832-4e3b-8543-37d33ad6a251" />

Then I will create a directory and copy files into it
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/ba40b0a2-c7ed-4136-8d24-53455287efe3" />

`mkdir LabFiles` used to create a new directory, it created a new empty directory called LabFiles.

You can use `cat` (to print everything), `less` (to scroll through), `head` (first few lines), or `last` (last few lines). 

the difference between `cp` and `mv`, `cp` copies a file, the original file remains and a duplicate is created at the destination while `mv` moves or renames a file, the original file is removed from the old location and placed at the new location. 

Now I will move on to create and run a Bash Script. I will first create the script file, then add the shebang and script content followed by making it executable and run the script. 
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/40465d48-89a2-49b0-b8eb-76d7f6c00cb1" />
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/9505b0a8-0ef7-4be0-a94d-31e865caf5d3" />
<img width="1434" height="1018" alt="image" src="https://github.com/user-attachments/assets/558b0151-dcc1-446d-914a-552531abd133" />

`chmod777` is used to set the permission so that the file can be read, write, and executed, allowing the system to run it as a program, without this, you cannot execute the script with `./hello_world.sh`. The `#!/bin/bash` tells the system which interpreter to use to run the script. `/bin/bash` means use the Bash shell. Without it, the system may try to run the script with a different shell, causing errors.

Now I will do a loop and conditional script, I will first create the script, make it executable and run it, the program will capture user input from 1 to 10 and validates it, if conditions are correct, it will show the system info, if a value outside of 1 to 10 is caputred, it will return an error. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/e090ef3c-2b7b-4a34-a786-2e2eb3375ead" />

Testing the limits with number less than 0 and more than 10. 

<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/ad19ff08-522d-4f2f-8c67-763af4526c91" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/8abb9ec5-c72b-4344-b712-0b93bd6c757f" />

the `for` loop iterates over a list of values. In my script, `for I in 5 4 3 2 1` runs the loop 5 times, with `I` taking each value in order. The `sleep 1` pauses for 1 second between each loop. The script checks for number greater than 10 using `if [ $user_number -gt 10 ]`, prints an ERROR message, and skip the system info part. The valid input can be handled better using a `while` loop to keep asking the user for a number until a valid number is entered. 

Now I will do a system monitoring script, which includes a number of cycles to run, at a set interval. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/3719d626-f6cd-4de7-bf71-294e20447807" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/c7c4ebe3-85eb-4f27-a376-fc82466bcc25" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/17c8c3d2-6d9d-4b02-b8a7-2b361c1ed33b" />

The `free -h` shows system memory usage in human readable format, it displays total, used, free, shared, buff/cache, and available memory. I could add in commands like `netstat -i` to show network interface statistics or `ss -tulpn` to show listening ports, I could also add in `ping -c 4 google.com` to check connectivity and latency. Automations like this saves time, reduces human error and ensures tasks are performed consistently. Instead of manually typing the commands every hour to check, an admin can just schedule a script with `cron` to run automatically and alert them if there's any issues. This is critical for monitoring 24/7 for production servers. 

# Lab 2b reflection. 
Creating a web server using AWS EC2 is so different from running Ubuntu in my local VMware Workstation. The entire process from signing up for AWS to seeing the EC2 Apache default page from my own browser in my VMware feels like I was actually building part of the internet. The most challenging part was understanding network security. I initially forgot to open port 80 in the Security Group, so my browser timed out. After adding the HTTP rule, the page loaded successfully. Even though Ubuntu's UFW was later configured, the AWS firewall was the first line of defence. Using SSH with a key pair was another new experience. On my local VM, I just used a username and password. Here, I have to manage the .pem file and set correct permissions (chmod 400). This taught me the real-world practice of securing cloud servers, passwords are rarely used in production. Cost control was also something new to me. I set up a budget alert and made sure to stop the instance after completing the lab. This exercise made me appreciate why cloud engineers are so careful about resource lifecycle management. Overall, this lab made me understand how websites are actually hosted, how firewalls work at both the cloud and OS level, and why SSH key pairs are the industry standard for secure remote access. I feel more confident managing cloud resources and exploring other AWS services. 

Bash scripting for system automation taught me that scripts can turn a series of long manual commands into a single executable file, saving both time and effort, and reducing errors. The `for` loop and `if-elif-else` conditions gave me control over how to script flows, I could add in count downs, validating user inputs, and display different outputs based on the conditions set. The resource monitor script showed how adminds can automate checks for memory, disk, and processes, which is essential for maintaining servers. I also learned about file permissions, without `chmod 777`, scripts wont be able to run. This experience has made me realise that automation is not just a convenience but a fundamental skill for any system admin. 

============================================================================================

# Lab 3a. DNS setup and SSL configuration. 

In this lab, I will be using DuckDNS to register a domain name for my AWS EC2 Ubuntu server, configure apache, and securing my site with Let's Encrypt SSL/TLS certificate using Certbot. I already have an AWS EC2 instance running, apache 2 installed and working as well as a security group that allows SSH(port 22), HTTP(port 80), and HTTPS(port 443). DuckDNS provides free dynamic DNS records, allowing me to map a hostname to my EC2's public IP without purchasing a domain.

First I go to DuckDNS.org to get a free domain and name it hakuverse. 
<img width="1347" height="1006" alt="image" src="https://github.com/user-attachments/assets/dae5748e-14c6-4b8f-ac39-55fd175c1d2b" />

To create the DuckDNS IP update script on my EC2 instance, I ran my EC2 instance and SSH into my EC2 using my VMware Workstation. 
<img width="1377" height="738" alt="image" src="https://github.com/user-attachments/assets/b10baf68-d21e-4340-af45-d59cd394bab3" />
<img width="1402" height="212" alt="image" src="https://github.com/user-attachments/assets/37d34555-dcd1-495c-be7c-4a27dcf70d05" />

I then create the update script and check if it runs properly
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/6df2b75d-9ff4-4729-a1b7-f0a8a37311d7" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/adc125c3-8fa8-45d6-b2d1-1d58ecc5f61a" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/1845156b-65d2-4cad-ab78-12e736e26410" />

Now I will set up automatic IP updates with cron and verify DNS resolution
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/f4a7dd98-461f-411c-b9a3-23db0e2ec5a9" />

Success showing my EC2 instance's public IP address `3.107.16.201` instead of `210.10.77.59`
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/c4447183-8d42-4764-83a6-879d644bbec5" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/a9a8b3c5-8109-46b9-b36c-b347da01a20a" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/61c22518-5676-4c40-ab05-10ffc7d11ce4" />

Now I will install certbot, verify the installation, obtain SSL certificate with certbot and test HTTPS in browser. Currently only HTTP is allowed to access my `hakuverse.duckdns.org` because I do not have an SSL certificate installed for my port 443 (HTTPS), I will install certbot and try again after getting an SSL certificate. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/a0d12760-0f85-4d5f-a9fc-c20ec7e23c32" />

I install certbot using `sudo apt install certbot python3-certbot-apache -y` and verify with `certbot --version`
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/5b1a313b-58a2-466b-be31-8cd9b3d9c9b1" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/8bcbe9b1-d915-45e6-ac0f-fe4502b7c0cb" />

Now I will run Certbot in Apache mode and get my SSL certificate
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/cf4437a0-53d5-4565-9768-ca12b3c8cd21" />

Time to test if it works on HTTPS now. (It works!) 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/cfc23998-5427-4edf-b444-eeb93dfe4446" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/855fab04-2acc-499a-a4bb-5aad8121b06b" />

Now I test for a dry run of certificate renewal since Let's Encrypt certificates are valid for only 90days, and I check the renewal timer.
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/70fb2a3f-5ca4-4478-9569-fc50b24ffc41" />

Now it is time to stop my EC2 instance after finishing this lab to save money. It is very important to stop or terminate any EC2 instance when not using. 
<img width="1426" height="237" alt="image" src="https://github.com/user-attachments/assets/28228724-2b9f-4ff3-b809-2486422b86ea" />
<img width="697" height="108" alt="image" src="https://github.com/user-attachments/assets/76773db7-7914-4fc6-a50e-b713899f7e16" />

# Lab 3a reflection. 
DNS (Domain Name System) translates human readable domain names like `hakuverse.duckdns.org` into machine readable IP addresses. Without DNS, users would need to remember and type the IP address to visit websites. 

DNS propagation takes time because DNS records are cached by many servers around the world. When record is updated, it takes time for the cache to expire and refresh with new information. This process can take minutes or hours, depending on the settings. 

Let's Encrypt uses the ACME protocol. Certbot creates a temporary verification file on my server at a specific URL. Let's Encrypt then tried to access that file via HTTP. If it can access, it confirms that I have the control over my domain and issues the certificate to me. 

If a certificate expires and is not renewed, serious problems could occur, which includes browser warnings, like "your connection is not private" security warnings, or a loss of trust, when the padlock icon disappears and replaced with a 'not secure' message. It could also lead to data exposure as the traffic between the user and the server becomes unencrypted, so sensitive data like passwords or personal information can be intercepted and read by attackers.

The risks if TLS is not configured on a public-facing site includes, 1. All data (passwords, personal info, etc) is sent in plain text and can be intercepted. 2. Users cannot verify that they are connecting to the real site which is vulnerable to phishing. 3. Browsers will show "Not Secure" warning messages, reducing user trust in the website. 

If I leave my cloud VM running for month, I will incur a huge costs as it is a pay-per-use server, also it could lead to security risks that an unattended cloud VM might be compromised. 

============================================================================================

# Lab 3b. Bash Backup Scripting, Cron Jobs & Cloud Export 
In this lab, we will be focusing on creating a Bash script that backs up files from `~/Documents` to `~/backup`, compress the backup with a timestamp, transfers it to my AWS EC2 cloud server via SCP and it runs automatically every hour using cron. 

First I copy my `Hakuverse.pem ` to my `.ssh` directory and set the correct permissions. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/7b938a13-2b9f-428a-a33e-66caf14a7dbb" />

Next I will run some basic Bash command exercises. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/25e7fe63-8b26-4fdb-9b19-5d5de47f4b74" />

Now I will create test files and directories 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/81f2809c-6474-48a8-b860-393e26b0787b" />

Now I am going to create the basic backup script, set permission, and make it executable and test it. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/75681a32-3eef-4afe-8517-31ddfc6e3424" />

Now all the files in my Document folder is being backed up into the backup folder. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/c37803fb-8f7e-4bf2-8f52-25405bc0240d" />

Next, I am moving the script to /usr/bin and test running `testscript` from /tmp directly. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/7696e2ab-dd66-48ef-95b5-6a7c94003578" />

I will now add timestamp and ZIP compression to the script and test the updated script 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/d095ba5a-287d-4de7-9974-6895f92827c3" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/54a5f08e-404c-4936-b0f7-7b61fa926009" />

I will now proceed to set up Cron Job and verify it and simulate multiple backups to check. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/e6521b03-9299-4dde-8602-6a09d1229fc6" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/181fd665-dc9d-4a88-8a55-a64208790983" />

Now I will add SCP to export to my AWS EC2 server, before that I need to start my instance and ssh into my aws ec2 first.
<img width="1717" height="1392" alt="image" src="https://github.com/user-attachments/assets/35ee97c2-24e6-404d-9fbd-f35da6b8bcac" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/6a0e8f27-f8c4-4e47-ab75-8e4dff15e0c8" />

Now I will update the script with SCP and run it 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/02a24c9c-8576-481e-beb6-dcd4e1c6bb04" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/00e9e261-c1ec-4069-a790-eae7eaab31f1" />

Now we move back to ssh on my EC2 instance and check the file using `ls -lh ~/*.zip`. We can see the backup is on my AWS EC2 now.
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/b21a7085-69a6-43bb-9af6-e804e3af1ba1" />

I will say it over and over again, once you are done with the Cloud server, please please please REMEMBER TO CLOSE/TERMINATE IT once youre done using it!!! 
<img width="1390" height="625" alt="image" src="https://github.com/user-attachments/assets/e4d61040-2ab4-4fdf-b852-5d6734dbc296" />

# Lab 3b reflection. 
Absolute path are critical for cron because cron runs in a minimal environment with a restristed path, so it is to ensure that scripts never fails, automating this with cron ensures the backup runs every hour without human intervention too. This consistency is impossible to achieve with sys admin manually executing and is vital for production servers. 

This lab showed me how system adminstrators automate repetitive tasks. I wrote a Bash script that backs up files, adds a timestamp, and compressed them into a ZIP archive. Automating this with cron was a game changer, I set the interval to run every hour, ensuring continous protection of the test files without any manual effort. I also added SCP to export the backup to the cloud, it helps in critical situations like a distant disaster recovery method. The biggest lesson was that automation isnt just about saving time, its about consistency and reliability. A cron job never forgets to run, unlike human tends to make mistakes sometimes. This lab gave me practical skills in scripting, scheduling, and secure file transfer that are essential for any sys admin or devops role. 


============================================================================================

# Lab 4. Additional Server Service (Docker) 
I will deploy an additional server service using Docker. Docker is the industry standard for containerized application deployment which is used by companies like Netflix, Uber, and Spotify. I will install Docker on my EC2 instance, Run an Nginx web server container, customize the container with my own HTML page, connect Docker to my DuckDNS domain using a reverse proxy. 

First I will need to start my AWS EC2 instance and access it thru my local VMware. 
<img width="1397" height="663" alt="image" src="https://github.com/user-attachments/assets/d5f0f14f-c3cc-4c27-9691-97d7aacd1e3c" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/6e87384a-1253-4413-aa98-2faed095b5ab" />

Then I'll update systen and install, start and enable Docker. I will also verify it and test out by using `sudo docker run hello-world`
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/591b3cc0-2012-4ebe-b053-04f4e9b953ef" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/7e9c011b-c8ef-43ab-9c9d-475b13ae695f" />

Now I will allow non-root docker usage to avoid typing sudo everytime.
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/8180816d-ada7-46ab-9b93-aaefa4cc9639" />

Now I will run my first container (Nginx web server) and verify if the contain is running.
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/73c2f197-a0fa-4e36-88a4-e771d3b8c7e8" />

Then I test the Nginx container locally with curl and in browser using `http://32.236.177.46:8080` 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/bb2ab80c-78d3-4f06-8119-3786a9c42bff" />
I forgot to add in port 8080 in my AWS EC2 and it shows unable to connect, after setting my security group in AWS console and add in inbound rules to include port 8080 it is now successfully loaded. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/eb243311-e674-4a4c-9ed6-a5bdc5ba5d99" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/aebbb2b2-17dd-4b5e-b8fc-f1327b20eb9c" />

Now I will customer the container with my own HTML page. 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/ef6dcb5f-bbef-41d1-b89b-d53df1bb38e0" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/5209dec1-d4d3-4b4d-9abe-efde2beb5800" />

I will try out the container management commands now 

View container logs 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/104df5a0-a12b-4bbd-b186-a287ef40b44e" />

Stop the container, start it back, check container status 
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/099fb18c-b025-41a0-b106-f089962b7cb7" />

Now I will connect Docer to my DuckDNS Domain, so instead of using `http://32.236.177.46:8080`, I can make my Docker container accessible via my DuckDNS domain using apache as a reverse proxy.
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/effbd134-f3da-4446-860f-d72408bff1ad" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/5312b9cf-c8f1-479f-ba12-298bd8072c8f" />
<img width="1524" height="1076" alt="image" src="https://github.com/user-attachments/assets/1a151de3-8d70-4f35-9bb1-f9234fb55a4d" />

# Lab 3b reflection. 
So why Docker over traditional installation? Docker packages on application with all its dependencies, libraries, and configuration files into a single container. This eliminates the whole "it works on my computer" scenario altogether. Docker also makes it easy to run multiple versions of the same application witout conflicts. 

The benefits of containerization includes
1. Isolation, each container runs its own environment with its own filesystem.
2. Protability, contain run the same on any system with Docker installed.
3. Resource Efficiency, containers shares the same host kernel which is lighter than virtual machines.
4. Reproducibility, the same docker image runs the exact same way everywhere.

Running on Nginx container on AWS EC2 demonstrated the DevOps workflow. I built a container, exposed it via port mapping, and even connected it to a domain using a reverse proxy. This is similar to how companies deploy microservices in production where each service runs in its own container and is independently scalable. I deployed an Nginx web server inside a Docker container, Nginx is a high-performance web server and reverse proxy widely used in production environments. Using Docker, I was able to start the server with a single command `docker run`, customise it's content by copying files into the container, and even expose it through my domain using Apache as a reverse proxy. 

Deploying Docker on my AWS EC2 instance was one of the most practical exercise in this course. I installed Docker, ran an Nginx container, and had a web server running in less than 5mins, this would take way longer if I was to do it with a traditional apache installation. The `docker run` command is incredibly powerful, it downloads the image, creates container, maps ports, and starts the service automatically. Copying my own HTML file into the container showed how easy it is to customise containerised applications. I also learned that containers are isolated, my Nginx container runs independently of the system's Apache, each on different ports. Thi experience gave me confidence to explore other stuffs like MariaDB, or WordPress in the future. Docker is clearly the foundation of mordern DevOps, and understanding it is essential for any cloud or system admin role.


This is the END of my GitHub for BRG30-ISEA-Labs 
Thanks for Reading! 
Signing out
Hakuverse
CT0390892
============================================================================================
