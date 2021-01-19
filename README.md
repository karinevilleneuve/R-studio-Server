Step by step to help you download R and R Studio on Ubuntu server 18 using the command line

# Install R base

You need to add this line in your **/etc/apt/sources.list** file

```{bash, eval=FALSE,}
deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran40/
```

There was an issue with a second key found on the Ubuntu keyserver. The Ubuntu archives on CRAN are signed with the key of “Michael Rutter marutter@gmail.com” with key ID 0x51716619e084dab9. To add the key to your system with one command use :

```{bash, eval=FALSE}
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
```

To install the complete R system, use

```{bash, eval=FALSE}
sudo apt-get update
sudo apt-get install r-base
sudo apt-get install r-base-dev
```

Launch R to make sure your R is 4.0. or higher

```{bash, eval=FALSE}
> R
R version 4.0.3 (2020-10-10) -- "Bunny-Wunnies Freak Out"
Copyright (C) 2020 The R Foundation for Statistical Computing
Platform: x86_64-pc-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

```

# Install R Studio serveur 

```{bash, eval=FALSE}
sudo apt-get install gdebi-core
wget https://download2.rstudio.org/server/bionic/amd64/rstudio-server-1.3.1093-amd64.deb
sudo gdebi rstudio-server-1.3.1093-amd64.deb
```

# Launch R Studio 

paste this in your web browser and replace *<server_id>* with the IP adress of your server. 

```{bash, eval=FALSE}
http://<server_id>:8787
```

**To get the IP adress of your server**

```{bash, eval=FALSE}
hostname -I
```
For exemple, I would type the following in my web browser : http://123.456.78.910:8787

You will be redirected to a page asking you for you username and password (these are the same you use to log into your server)

# Start, stop, and get the status of rstudio-server

```{bash, eval=FALSE}
sudo rstudio-server start
sudo rstudio-server stop
sudo rstudio-server status
```

# Troubles connecting to Rstudio throught your browser 

We couldn't connect with a browser because the port 8787 was blocked by a firewall. I removed this firewall with the following commands:

```{bash, eval=FALSE}
sudo firewall-cmd --permanent --zone=public --add-port=8787/tcp
sudo firewall-cmd --reload
sudo ufw allow 8787
``` 

# Download library and packages in R Studio 

Write the following in the **terminal** of your R studio page (not the R console)

```{bash, eval=FALSE}
sudo apt install build-essential libcurl4-gnutls-dev libxml2-dev libssl-dev
```

# References

- https://rstudio.com/products/rstudio/download-server/debian-ubuntu/ 
- https://cran.rstudio.com/bin/linux/ubuntu/README.html 

