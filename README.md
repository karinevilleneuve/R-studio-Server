Step by step to help you download R and R Studio on Ubuntu server 18 and over using the command line. 

# Install R base

You need to add this line in your **/etc/apt/sources.list** file.

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

Your IP adress will be located after the second **inet** and will most likely be in this format **123.456.78.910**

```{bash, eval=FALSE}
> ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 123.4.5.6/7 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether a8:5e:45:69:65:d1 brd ff:ff:ff:ff:ff:ff
    inet 123.456.78.910/26 brd 132.208.64.255 scope global dynamic noprefixroute eno1
       valid_lft 396949sec preferred_lft 396949sec
    inet6 fe80::25d8:a074:3cd9:ceae/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```
So I would type the following in my web browser : http://123.456.78.910:8787

You will be redirecte to a page asking you for you username and password, and this are the same you use to connect yo rou server. 

# Download library and packages in R Studio 

Write the following in the **terminal** of your R studio page (not to R console)

```{bash, eval=FALSE}
sudo apt install build-essential libcurl4-gnutls-dev libxml2-dev libssl-dev
```


# References

- https://rstudio.com/products/rstudio/download-server/debian-ubuntu/ 
- https://cran.rstudio.com/bin/linux/ubuntu/README.html 

