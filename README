# Scripts for obtaining and renewing letsencrypt ACME2 (wildcard) certs

These 2 bash scripts help in obtaining and renewing Letsencrypt SSL certs for domains managed by dnsimple

It is not necessary to install certbot, as we use the docker images for these

These script only obtain the certificates, and do not configure your webserver.

## Requirements

* Docker
* dnsimple API key

## Usage

    git clone https://github.com/ianwhite/dnsimple-letsencrypt .
    
    # to obatin a wildcard cert
    sudo dnsimple-letsencrypt/get-wildcard-cert your.domain

    # follow the instuctions to place the API key in the specified directory

    sudo dnsimple-letsencrypt/get-wildcard-cert your.domain

    # sometime later

    sudo dnsimple-letsencrypt/renew-all-certs --dry-run

## Automating via cron

Once it's all working setup your cron script as follows (here assuming you're using nginx)

   sudo crontab -e

And add a line like the following (replace /PATH/TO and the contents of the renew hook)
   
   6 1,13 * * * /PATH/TO/dnsimple-letsencrypt/renew-all-certs --renew-hook "service nginx restart"

