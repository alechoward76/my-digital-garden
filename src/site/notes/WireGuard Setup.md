---
{"dg-publish":true,"permalink":"/wire-guard-setup/"}
---

Step 1: Install Docker on Droplet
  - I followed this guide to set up docker on my droplet: https://thematrix.dev/install-docker-and-docker-compose-on-ubuntu-20-04/
  - I ran this command to install the tools needed: sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
  - I then ran this command to add a docker key: curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  - I ran this command to add the Docker repo for 32 / 64 bit OS: sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   - I switched to the above repo using this: apt-cache policy docker-ce
   - I installed Docker: sudo apt install docker-ce -y
   - Then I installed Docker Compose: sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o     /usr/local/bin/docker-compose
   - Finally, I just had to set proper execute permissions: sudo chmod +x /usr/local/bin/docker-compose

Step 2: Install Wireguard on Droplet
   - I followed this guide for the Wireguard setup: https://thematrix.dev/setup-wireguard-vpn-server-with-docker/
   - I created directories in the following path: ~/wireguard/config/
   - Then, I created a docker-compose.yml file and edited it as seen below in this path: ~/wireguard/docker-compose.yml
   ![docker_compose_yml.jpg](/img/user/docker_compose_yml.jpg)
   - I navigated to the wireguard directory and used this command to start wireguard: docker-compose up -d
   - I ran this command to generate a qr code to open a tunnel for my phone: docker-compose logs -f wireguard
   ![PHONE.png](/img/user/PHONE.png)
  
  IP Without VPN: 
   ![phone_ip1.png](/img/user/phone_ip1.png)
   
   IP With VPN:
   ![phone_ip2.png](/img/user/phone_ip2.png)
   
   - I copied the config file for pc1 and used it to open a tunnel on my  laptop for wireguard for Windows
  ![WIN_CONF_ACTIVE.jpg](/img/user/WIN_CONF_ACTIVE.jpg)
  
  IP Without VPN: 
   ![ip1.jpg](/img/user/ip1.jpg)
   
   IP With VPN:
   ![vpn_ip.jpg](/img/user/vpn_ip.jpg)
