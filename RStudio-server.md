
RStudio Server enables you to provide a browser based interface (the RStudio IDE) to a version of R running on a remote Linux server. Deploying R and RStudio on a server has a number of benefits, including:

- The ability to access your R workspace from any computer in any location;
- Easy sharing of code, data, and other files with colleagues;
- Allowing multiple users to share access to the more powerful compute resources (memory, processors, etc.) available on a well equipped server; and
- Centralized installation and configuration of R, R packages, TeX, and other supporting libraries.
(https://support.rstudio.com/hc/en-us/articles/200552306-Getting-Started)



security - port 8787

launch instance

"  Rstudio_server_eRSA_Jan2016  "

`sudo chown ubuntu /mnt`
`sudo passwd ubuntu`
`ln -s /mnt ~/Mounted_Storage`

## RStudio-server


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
sudo rstudio-server verify-installation
less /var/log/syslog 
sudo rstudio-server license-manager status
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
