# ft_onion

## Objectives

The goal of this project is to create a web page and make it accessible from the Tor network by creating a hidden service. The hidden service is a web service that hides on the Tor network.  

**Mandatory:**
You must run a web server that shows a webpage on the Tor network.  
• The service must have a static web page: a single index.html file. The page will be accessible through a url of the type xxxxxxxxx.onion. The content displayed on the page is up to you.  
• Nginx will be used to configure the web server. No other server or framework is allowed.  
• Access to the static page via HTTP on port 80 must be enabled.  
• Access to the server via SSH on port 4242 must be enabled.  
• You should not open any ports or set any firewall rules.  

**Bonus**
You can enhance your project with the following features:  
• SSH fortification. It will be thoroughly tested during evaluation.  
• An interactive application, something more impressive than a static webpage.  

## My solution

### Mandatory

#### Virtual Machine  
Firstly I [created a Debian virtual machine using Oracle VM VirtualBox](https://github.com/gemartin99/Born2beroot-Tutorial/blob/main/README_EN.md).  
In my VM I installed some basic packages to make my job easy like:
- installing VIM: so I do not need to suffer with nano;
- installing sudo: so I can use my user instead of root.

#### SSH install and configuration
Then I [set the SSH](https://github.com/gemartin99/Born2beroot-Tutorial/blob/main/README_EN.md#42---installing--configuring-ssh-) to the port 4242.

#### NGINX install and configuration

To install NGINX:
```
sudo apt install nginx
```

After it was installed I changed its configurations following this two references:  
[Raj Matariya - Medium](https://medium.com/adrixus/beginners-guide-to-nginx-configuration-files-527fcd6d5efd)  
[Blockchain Made Simple](https://www.youtube.com/playlist?list=PLGd6Pjf07X7ii1Mhfiq9g6m1NDGg0eDRg)

```
sudo vim /etc/nginx/...
```

#### Static webpage creation

#### TOR install and configuration  

To install and configure TOR I followed the basic tutorial from the [TOR project website](https://community.torproject.org/onion-services/setup/).  
Installing:  
```
sudo install tor
```
Configuration on torrc:
```
sudo vim /etc/tor/torrc
```
Adding my hidden service on torrc:
```
HiddenServiceDir /var/lib/tor/ft_onion/
HiddenServicePort 80 127.0.0.1:80
```
After saving the torrc file, restart the tor service and get the hostname(xxxxxxxx.onion link):
```
sudo systemctl restart tor
sudo cat /var/lib/tor/ft_onion/hostname
```

### Bonus

#### SSH fortification

#### Dynamic webpage creation
