<p align="center">
<img src="https://i.imgur.com/QiwmfwB.png"/>
</p>

<h1>Build Your Own Secure Search Engine on a Linux Virtual Machine (Azure)</h1>
This tutorial will demonstrate how to build your own secure search engine that you can host on a Linux Virtual Machine Server. SearXNG is a Metasearch engine that uses existing search engines and builds a random search profile for each search. As a result, ad profiles cannot be created which means you will not experience any ads! <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- CMD / Bash
- Docker
- Git

<h2>Operating Systems Used </h2>

- Linux Server (Ubuntu 20.04)
- Windows 11 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Build a Linux cloud server on Azure
- SSH onto Linux server and download all the needed software (Docker, Docker Compose, SearXNG, Git, etc.)
- Purchase a Domain
- Point A record of domain to the IP of VM
- Run Basic Linux commands to configure search engine to your domain 

<h2>Deployment and Configuration Steps</h2>

<p>

  ![Screenshot 2023-09-04 200012](https://github.com/JCallerx/secure-search/assets/143349237/c376b477-9f7c-4c62-aa51-6decc4149c6c)

</p>
<p>
"Begin by deploying a Linux server on Microsoft Azure, utilizing as many resources as you consider necessary. Set a username and password that you will remember (you will need this information to SSH into your virtual machine). Once the server is deployed, open the Command Prompt on your Windows machine and enter the following command: ssh (username)@(IP of Virtual Machine), for example: ssh rxlab@192.168.30.16. Execute this command and enter your password when prompted. You should now be successfully connected to your Linux server. Once connectected it is best practice to update Linux repositories by running the command "sudo apt update && sudo apt upgrade -y"  to ensure you are on the latest, most secure repositories "
</p>
<br />

![Screenshot 2023-09-04 200425](https://github.com/JCallerx/secure-search/assets/143349237/ac769c47-1773-4a40-9f26-287781261a9c)
<p>Now we will install all the necessary software needed to host your search engine. As seen above we will begin by installing docker using the command "sudo apt install docker.io -y"</p>

![Screenshot 2023-09-04 200552](https://github.com/JCallerx/secure-search/assets/143349237/04f36204-cdeb-476f-8a18-2c0768079383)
<p>Next, let's install docker compose by using the command "sudo apt docker-compose -y". This will allow us to run multiple Dockers at once.</p>

![Screenshot 2023-09-04 202014](https://github.com/JCallerx/secure-search/assets/143349237/5d909981-d783-4dd8-8dc2-16820a2408d6)

<p>
After installing Docker compose we will change directories by using command "cd /usr/local". This is where your SearXNG files will be installed. Run the next commands as follows tho install Git and SearXNG subsequently: "sudo apt install git -y" then "sudo git clone https://github.com/searxng/searxng-docker.git"
</p>
<br />


![Screenshot 2023-09-04 200947](https://github.com/JCallerx/secure-search/assets/143349237/f484b970-01d4-476f-ac0b-20b8f4860dbf)

<p>
After installing all the required software, acquire a domain name that you will use to host your search engine.
</p>
<br />

![Screenshot 2023-09-04 201517](https://github.com/JCallerx/secure-search/assets/143349237/9e452dc4-5b62-4fcd-acf5-1233efa11d40)
<p>Once you have purchased your domain, you will need to point the A record of the domain to the IP address of your virtual machine on Microsoft Azure by navigating to the DNS settings on the Domain broker.</p>

