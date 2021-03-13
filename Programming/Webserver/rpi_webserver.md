# Raspberry Pi Webserver
## Description 
Information for setting up a secure (https) webserver using a raspberry pi, nginx, certbot and a DNS provider. Followed tutorial from https://youtu.be/OWAqilIVNgE with modification (using rpi instead of cloud service provider). Other good resource https://youtu.be/QdHvS0D1zAI.
## Proxy Server
### nginx 
1. Reverse proxy server (TCP/UDP)
2. Homepage: https://nginx.org/en/
3. Tutorial: https://pimylifeup.com/raspberry-pi-nginx/
#### Installation 

```bash
sudo apt-get remove apache2 # Ensure apache2 is not installed
sudo apt-get install nginx
```

#### Setup
Copy the default nginx configuration to a new configuration:
```bash
cp /etc/nginx/sites-available/default /etc/nginx/sites-available/*site_name*
```
Edit the newly created file to display the following:
```
server {
	listen 80;
	listen [::]:80 ;
	
	root /var/www/*website_file_dir*;

	index index.html index.htm index.nginx-debian.html;

	server_name *your_website_address*;

	location / {
		try_files $uri $uri/ =404;
	}
```
Put newley created configuration into enabled sites directory:
```bash
ln -s /etc/nginx/sites-available/*sitename* /etc/nginx/sites-enabled/
```
Make directory that holds website files (index.html etc.):
```bash
mkdir /var/www/*site_name*
cd /var/www/*site_name*
touch index.html # Create and edit file as needed
```

#### Commands	
```bash
sudo systemctl start nginx # Start Server
sudo systemctl status nginx # Server status
sudo systemctl stop nginx # Stop server
sudo systemctl restart nginx # Reboot server
sudo killall nginx # Stop all processes
```

## HTTPS Certificate
Gives website a certificate of security that browsers can recognise.
### certbot
#### Installation
```bash
sudo apt-get install certbot python-certbot-nginx
```
#### Setup
```bash
sudo certbot --nginx
```
1. Enter email
2. Agree to terms
3. Dont share email
4. Select https addresses
5. Redirect http to https

#### Commands
Certbot certificate expires every six months
```bash
sudo certbot renew # Renew certificate
```

## Port Forwarding
Need to setup port forwarding on router.
```bash
ip route # Find router address (LINUX)
```
Type address in browser, navigate to port forwarding and add:
- Protocol: TCP
- WAN port: 80
- LAN port: 80
- Desination IP: *local_ip_address*

May need to also set:
- Protocol: TCP
- WAN port: 443
- LAN port: 443
- Desination IP: *local_ip_address*

## Other Commands
```bash
hostname -I # Get local ip address
curl icanhazip.com # Public IPv6 address
curl ipv4.icanhazip.com # Public IPv4 address
```





