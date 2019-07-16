# Scripts for obtaining and renewing letsencrypt ACME2 (wildcard) certs

These 2 bash scripts help in obtaining and renewing Letsencrypt SSL certs for domains managed by dnsimple

It is necessary to install certbot, as I can't figure out a clean way of restarting nginx on the renew hook, as nginx is not in the docker container

These scripts only obtain the certificates, and do not configure your webserver.

## Requirements

### certbot

    sudo add-apt-repository ppa:certbot/certbot
    sudo apt-get update
    sudo apt-get install python-certbot-nginx

### certbot-dns-dnsimple

    sudo sudo apt-get install python-pip
    sudo pip install certbot-dns-dnsimple

### dnsimple API key

    Go here https://dnsimple.com/user and get one

## Usage

    git clone https://github.com/ianwhite/dnsimple-letsencrypt .

    # to obtain a cert
    sudo dnsimple-letsencrypt/get-cert your.domain

    # to obtain a wildcard cert
    sudo dnsimple-letsencrypt/get-wildcard-cert your.domain

    # follow the instuctions to place the API key in the specified directory

    sudo dnsimple-letsencrypt/get-wildcard-cert your.domain

    # sometime later

    sudo dnsimple-letsencrypt/renew-all-certs --dry-run

## Automating via cron

Once it's all working setup your cron script as follows (here assuming you're using nginx)

    sudo crontab -e

And add a line like the following (replace /PATH/TO and the contents of the renew hook)

    6 1,13 * * * certbot renew --renew-hook "service nginx restart"

