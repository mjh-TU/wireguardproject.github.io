# Cloud VPN Docker Proect

## Digital Ocean Account
    Went to Digital Ocean and created my account
## Set up VM on DO
    >Chose the Ubuntu 23.10 Droplet
    >Gave it the Shared CPU, regular SSD
  
    >Chose the 6$ per month option with 
      1 GB/1 CPU
      25 GB SSD
      1000 Transfer
      
    >Installed PuttyGen from here https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html and downloaded the msi file and installed
  
    >Created a Public and Private SSH keys using the puttygen using default settings and also once you click generate and that is done I added a passphrase for added protection
  
    >Then copied the public ssh key to the Digital Ocean site where it specifies it for your new machine so you can connect
  
    >Then Created the machine
  
    >Put the machine IP on putty and added the private key under the Connection->SSH->Auth, I put the user root in the section Connection->Data on putty as well
  
    >I then started the connection and entered my passphrase and was able to connect to the machine
  
## Install docker and wireguard
  
### Update machine, dont need sudo since I am using root (not a good idea but whatever)
      apt update
      apt upgrade
### Install instructions
    Used the instructions from https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-install-Docker-and-docker-compose-on-Ubuntu to install docker and docker-compose
  
    Had to use these instructions as I installed Ubuntu 23 and not Ubuntu 20.04
  
### Download the docker gpg file to Ubuntu
    sudo mkdir -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

### Add Docker and docker compose support to the Ubuntu's packages list
  
        echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-pluginsudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-pluginlinux/ubuntu   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

### Installed Docker compose using command
    apt-get install docker-compose

### Checked both were installed by just running the commands
    docker
    docker-compose

### Used the Instructions for Wireguard Install https://thematrix.dev/setup-wireguard-vpn-server-with-docker/
    Did not want to put the wireguard directory in root per the instructions putting it in home directory so I made a new directory in the home folder
            mkdir -p wireguard
            mkdir -p wireguard/config
    
### Created new file called docker-compose.yml for wireguard
    vim wireguard/config/docker-compose.yml
    
### Pasted the contents from the website to the yml file
    
### When you past the contents be sure to check and change the Timezone and Peers for what you desire
    I changed the timezone to America/Chicago by adding that to the file
    I changed peers=1 so I only have one user config
  
### Entered the directory where the docker-compose.yml is located and ran the command
    docker-compose up -d

  
## Verification
    To connect phone run the command
      docker-compose logs -f wireguard
    Install wireguard client on your phone and create a new using the QR code
    Install wireguard on your laptop
    To set up on my laptop I copied the contents of the conf file and pasted it into the wireguard application and named it

### Laptop
![image](https://github.com/mjh-TU/wireguardproject.github.io/assets/124700981/616fec19-9d2f-480e-abf0-f907573df83a)
![image](https://github.com/mjh-TU/wireguardproject.github.io/assets/124700981/05bfba99-f203-4684-b8e4-56a550cdf513)


### Phone
![image](https://github.com/mjh-TU/wireguardproject.github.io/assets/124700981/dc034e9e-5347-4627-9b30-c1800d84e555)
![image](https://github.com/mjh-TU/wireguardproject.github.io/assets/124700981/a57ec7d8-b46d-476d-8a8b-83ee4341fc90)
![image](https://github.com/mjh-TU/wireguardproject.github.io/assets/124700981/07327ae4-4650-43a0-991a-be609778f5f4)


### Docker containter running
<img width="470" alt="image" src="https://github.com/mjh-TU/wireguardproject.github.io/assets/124700981/130e720d-58c2-4cff-824b-11dee2296908">






