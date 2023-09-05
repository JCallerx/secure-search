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
Begin by deploying a Linux server on Microsoft Azure, utilizing as many resources as you consider necessary. Set a username and password that you will remember (you will need this information to SSH into your virtual machine). Once the server is deployed, open the Command Prompt on your Windows machine and enter the following command: ssh (username)@(IP of Virtual Machine), for example: ssh rxlab@192.168.30.16. Execute this command and enter your password when prompted. You should now be successfully connected to your Linux server. Once connectected it is best practice to update Linux repositories by running the command "sudo apt update && sudo apt upgrade -y"  to ensure you are on the latest, most secure repositories. 
</p>
<br />

![Screenshot 2023-09-04 200425](https://github.com/JCallerx/secure-search/assets/143349237/ac769c47-1773-4a40-9f26-287781261a9c)
<p>Now we will install all the necessary software needed to host your search engine. As seen above we will begin by installing docker using the command "sudo apt install docker.io -y".</p>

![Screenshot 2023-09-04 200552](https://github.com/JCallerx/secure-search/assets/143349237/04f36204-cdeb-476f-8a18-2c0768079383)
<p>Next, let's install docker compose by using the command "sudo apt docker-compose -y". This will allow us to run multiple Dockers at once.</p>

![Screenshot 2023-09-04 202014](https://github.com/JCallerx/secure-search/assets/143349237/5d909981-d783-4dd8-8dc2-16820a2408d6)

<p>
After installing Docker compose we will change directories by using command "cd /usr/local". This is where your SearXNG files will be installed. Run the next commands as follows tho install Git and SearXNG subsequently: "sudo apt install git -y" then "sudo git clone https://github.com/searxng/searxng-docker.git".
</p>
<br />


![Screenshot 2023-09-04 200947](https://github.com/JCallerx/secure-search/assets/143349237/f484b970-01d4-476f-ac0b-20b8f4860dbf)

<p>
After installing all the required software, acquire a domain name that you will use to host your search engine.
</p>
<br />

![Screenshot 2023-09-04 201517](https://github.com/JCallerx/secure-search/assets/143349237/9e452dc4-5b62-4fcd-acf5-1233efa11d40)
<p>Once you have purchased your domain, you will need to point the A record of the domain to the IP address of your virtual machine on Microsoft Azure by navigating to the DNS settings on the Domain broker.</p>

![Screenshot 2023-09-04 202339](https://github.com/JCallerx/secure-search/assets/143349237/3300d923-d397-4e7b-81d1-3a926eb13c7f)
<p>Now that you have purchased your domain we will run the final commands to finish the setup of your search engine:"ls" to list current directory. You should see a folder called searxng-docker. Change directories into this folder with the command "cd searxng-docker/".</p>

![Screenshot 2023-09-04 202444](https://github.com/JCallerx/secure-search/assets/143349237/41d6b1d7-77ba-49a9-9b6e-72d721693a27)
<p>Run command "ll" to view hidden files. You should now see a .env file. We will need to edit this file by using the command "sudo nano .env". </p>

![Screenshot 2023-09-04 202616](https://github.com/JCallerx/secure-search/assets/143349237/f803d7ef-f201-439d-a881-8ff43d7c6e23)
<p>Once we are inside the .env file we will edit this file by uncommenting (deleting #) on SEARXNG_HOSTNAME and inputting the domain name you have purchased after the =. Additionally you may uncomment  LETSENCRYPT_EMAIL and add an email address to generate an SSL certificate and encrypt your search engine.   </p>

![Screenshot 2023-09-04 203346](https://github.com/JCallerx/secure-search/assets/143349237/9796cffa-0350-4924-a800-811487c99c15)

<p>The last two commands you will run in order to launch get your search engine up and running will be the following: the first will generate a Secret Key that will go on your settings folder. Type in the command as follows: "sudo sed -i "s|ultrasecretkey|$(openssl rand -hex 32)|g" searxng/settings.yml". The second command will build our Docker environment by connecting 3 necessary docker containers. This will be the final command to launch your search engine. The command you eill type is "sudo docker-compose up -d".  </p>

![Screenshot 2023-09-04 204919](https://github.com/JCallerx/secure-search/assets/143349237/bacaaa12-b5fe-43d5-a64c-6d50a3854df7)
<p>"Congratulations! You now have your very own secure search engine, free of advertisements and data-mining ISPs. You should be able to open your browser and type in your domain, which will redirect you to SearXNG. Keep in mind that you can further configure your search engine to your preferences by adjusting your settings.yml file. Documentation for reference is available here: <a href="https://searx.github.io/searx/admin/settings.html" target="_blank">Documentation Link.</a> </p>
