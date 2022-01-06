# Updating Local Dev SSL Certificates

From manager container (or any ubuntu machine if you want to):
1. ```apt-get update```
1. ```apt-get install software-properties-common```
1. ```add-apt-repository ppa:certbot/certbot```
1. ```apt-get update```
1. ```apt-get install certbot```
1. ```certbot certonly --server https://acme-v02.api.letsencrypt.org/directory --preferred-challenges dns --manual```
1. Enter your work email, and Agree for TOS. 
1. For domains entry paste in:
    `````*.drumeo.com, *.musora.com, *.pianote.com, *.guitareo.com, *.guitarlessons.com, *.recordeo.com, *.singeo.com`````
1. Make sure you choose Y for the question about logging your IP otherwise this process will not work.
1. Follow on-screen guide, input data in to cloudflare DNs settings for all domains.
1. Once the command finishes, cert files are inside folder in your manager container /etc/letsencrypt/live/drumeo.com/
1. Nano edit and copy/paste from the terminal: ```nano /etc/letsencrypt/live/drumeo.com/cert.pem```  
   And paste in to all railenvironment files for all brands here: ```railenvironment/railenvironment_docker/alpine-apache-php-fpm-7/ssl/BRAND/ssl.crt```
1. Nano edit and copy/paste from the terminal: ```nano /etc/letsencrypt/live/drumeo.com/privkey.pem```  
   And paste in to all railenvironment files for all brands here: ```railenvironment/railenvironment_docker/alpine-apache-php-fpm-7/ssl/BRAND/ssl.key```
1. (the cert and private key are the same for all brands)
1. Once those ssl files are updated commit the changes to the environment repo.

**Once commited, all other devs must:**

1. Pull railenvironment repo
1. Go to railenvironment/railenvironment_docker folder -> run: sudo docker-compose build
1. go back to railenvironment folder -> run: ./rrr.sh