

**From the RStudio-Server page:**  
RStudio Server enables you to provide a browser based interface (the RStudio IDE) to a version of R running on a remote Linux server. Deploying R and RStudio on a server has a number of benefits, including:

- The ability to access your R workspace from any computer in any location;
- Easy sharing of code, data, and other files with colleagues;
- Allowing multiple users to share access to the more powerful compute resources (memory, processors, etc.) available on a well equipped server; and
- Centralized installation and configuration of R, R packages, TeX, and other supporting libraries.  
<https://support.rstudio.com/hc/en-us/articles/200552306-Getting-Started>


## Launch a virtual machine with pre-installed RStudio-Server

1. Log on to the NeCTAR dashboard <https://dashboard.rc.nectar.org.au/project>
1. Select the correct project allocation in the top bar (if it starts with "pt- ", it is your default trial allocation)
1. Select "**Access & Security**" under the "Compute" subheading in the left side main menu.
    1. Click "Create Security Group" 
    1. Name the security group 'RStudioServer', with the description "port 8787 and 22". Click "Create Security Group"
    1. Click "**Manage Rules**" in the "Actions" drop-down menu. 
    1. Click "**Add Rule**". Type "**8787**" under "**Port**". Under "**CIDR**", you choose a range of IP adresses that can access your VM through port 8787 (password protected). If you keep it as "0.0.0.0/0", you can access your VM from any computer, but anyone else might find a way to access it also. Here are the IP ranges for SA University networks. Use one of these, and the VM can only be accessed form a University computer (including an external computer using a VPN to access the University network).
        - 129.127.0.0/16 - University of Adelaide
        - 129.96.0.0/16 - Flinders
        - 130.220.0.0/16 - UniSA 
    1. Repeat the last step for port "**22**" (which allows SSH access to the VM)
    1. Select "**Key Pairs**" and use "**Import Key Pair**" to upload the public key of a keypair you have created in Putty (Windows users) or with `ssh-keygen -f ~/.ssh/keyname`. See <https://support.nectar.org.au/support/solutions/articles/6000055376-launching-virtual-machines> for instructions on setting up keypairs.
1. Select "**Images**" in the left side main menu. Click the "**Public**" tab at the top of the window.
1. Find the image named "**Rstudio_server_eRSA_Jan2016**" and select "**Launch Instance**" from the "Actions" drop-down menu.
1. Give your VM a name and choose a "**Flavor**" (size of the VM).
1. Select the "**Access & Security**" tab. Select your Key Pair name, and select the "**RStudioServer**" security group you just created.
1. If you might use a volume storage attachment at some point, select the "**Availability Zone**" and choose "**sa**" from the drop-down menu.
1. Click "**Launch**". It may take a few minutes for the instance to boot.

## Connect to the VM with SSH

See the support page:  
<https://support.nectar.org.au/support/solutions/articles/6000055446-accessing-instances>  

Copy the IP Address of the instance from the NeCTAR dashboard.
  - Windows - Set up a PuTTY connection with the IP address
  - Mac/Linux - In the terminal app, enter `ssh -i <keyname> ubuntu@<IPaddress>`


## Set up the RStudio-Server VM

There are a few shell commands that need to be run on the Instance after it has been launched as an initial set-up step.

If you are attaching a **Volume** storage block (highly recommended) to the VM, you should mount the storage to "**/mnt**" before performing the next step.  
Follow instructions <http://training.nectar.org.au/package07/sections/volumeStorage.html>

Use the following commands to learn about your VM disc structure:  
`lsblk ` , `df -hT ` , `htop `

To complete set-up, run the command:  
`bash Startup_Script.sh`

You will be prompted to provide a password for user: "ubuntu" . This password will be used to access the RStudio-Server through a web browser.

This script ensures the storage disc mounted at /mnt is writable, and provides a symbolic link to this disc in the home directory. The pre-installed RStudio-Server is started. The shell script then deletes itself as it is designed to only run once, at set-up.

        The commands to check the status and run RStudio-server are:  
        `sudo rstudio-server verify-installation`  
        `sudo rstudio-server status`  
        `sudo rstudio-server restart`  
        `sudo rstudio-server start`  
        `sudo rstudio-server stop`  

## Access RStudio in your web browser

In the address bar of your web browser, paste the IP address of your VM (fromt the NeCTAR dashboard: Instances page) followed by ":8787".  
`XXX.XXX.XXX.XXX:8787`

This should bring up the RStudio login window.
Enter the user : ubuntu  
and the password you set up.


sudo rstudio-server verify-installation
sudo rstudio-server status
sudo rstudio-server restart
sudo rstudio-server start
sudo rstudio-server stop



        sudo chown ubuntu /mnt
        ln -s /mnt ~/Mounted_Storage
        sudo passwd ubuntu
        
        
        sudo nano /etc/apt/sources.list
        sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
        sudo apt-get update
        sudo apt-get install r-base
        sudo chown ubuntu /usr/local/lib/R/site-library
        sudo apt-get install gdebi-core
        wget https://download2.rstudio.org/rstudio-server-0.99.489-amd64.deb
        sudo gdebi rstudio-server-0.99.489-amd64.deb
        rm rstudio-server-0.99.489-amd64.deb 
        sudo apt-get install texlive
        sudo apt-get install libcurl4-openssl-dev
        
        cd Mounted_Storage
        mkdir R
        
        
        
        
        install.packages("swirl")
        library(swirl)
        swirl()

        install_from_swirl("Getting and Cleaning Data")


sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9


sudo nano /etc/apt/sources.list
deb http://cran.ms.unimelb.edu.au/bin/linux/ubuntu trusty/

`sudo apt-get update`

`sudo apt-get install r-base`
##`sudo apt-get install r-base-dev`

sudo chown ubuntu /usr/local/lib/R/site-library

`wget https://download2.rstudio.org/rstudio-server-0.99.489-amd64.deb`
`sudo apt-get install gdebi-core`
`sudo gdebi rstudio-server-0.99.489-amd64.deb`


`sudo rstudio-server verify-installation`

https://www.rstudio.com/products/rstudio/download-server/

http://cran.ms.unimelb.edu.au/
deb https://<my.favorite.cran.mirror>/bin/linux/ubuntu trusty/
deb http://cran.ms.unimelb.edu.au/bin/linux/ubuntu trusty/
/etc/apt/sources.list

sudo nano /etc/apt/sources.list


??
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
sudo apt-key del E084DAB9


http://<server-ip>:8787


#troubleshooting

less /var/log/syslog 
sudo rstudio-server license-manager status
sudo rstudio-server verify-installation
sudo rstudio-server status
sudo rstudio-server restart
sudo rstudio-server start
sudo rstudio-server stop

sudo apt-get install texlive

sudo chown ubuntu /usr/local/lib/R/site-library


https://support.nectar.org.au/support/solutions/articles/6000098750-pawsey-installing-r-and-rstudio-in-the-cloud


#! /bin/bash

sudo chown ubuntu /mnt
sudo chown ubuntu /usr/local/lib/R/site-library
ln -s /mnt ~/Mounted_Storage
sudo passwd ubuntu
sudo rstudio-server verify-installation
cd Mounted_Storage
mkdir R
echo "Set-up is complete. Deleting Startup_Script.sh
wait && rm Startup_Script.sh


sudo apt-get install texlive-latex-extra
