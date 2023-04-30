[![Docker build latest](https://github.com/eftechcombr/postfix/actions/workflows/docker-publish-latest.yml/badge.svg)](https://github.com/eftechcombr/postfix/actions/workflows/docker-publish-latest.yml)
[![Docker build dev](https://github.com/eftechcombr/postfix/actions/workflows/docker-publish-dev.yml/badge.svg?branch=dev)](https://github.com/eftechcombr/postfix/actions/workflows/docker-publish-dev.yml)


# postfix

## Images

 - [x] eftechcombr/postfix:latest
 - [ ] eftechcombr/postfix:mailgun
 - [ ] eftechcombr/postfix:mailgun-europe
 - [ ] eftechcombr/postfix:ses
 - [ ] eftechcombr/postfix:gmail
 - [ ] eftechcombr/postfix:office365
 - [ ] eftechcombr/postfix:sendgrid
 - [ ] eftechcombr/postfix:locaweb
 

Postfix SMTP Relay

## run

    docker run --rm -d --name postfix \
    -e RELAY_USER=postmaster@domain \
    -e RELAY_PASS=xxxxxxxxx \
    -e RELAY_HOST=smtp.mailgun.org \
    eftechcombr/postfix:latest

## docker-compose

    version: '3.2'
    services:
      relay:
        image: eftechcombr/postfix:latest
        restart: unless-stopped
        volumes: 
         - postfix-volume:/var/spool/postfix
        ports:
         - "30025:25"
        environment:
         RELAY_USER: postmaster@XXXXXXXXXXXXXXXX
         RELAY_PASS: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
         RELAY_HOST: smtp.mailgun.org
    volumes:
      postfix-volume:
      
      
> docker-compose up -d


 # testing

    echo "Email Test" | mail -s "This is a simple test" contato@eftechcombr.com.br
 
or

    sendmail -f sender@example.com recipient@example.com
    From: Sender Name <sender@example.com>
    Subject: Amazon SES Test                
    This message was sent using Amazon SES.                
    .




