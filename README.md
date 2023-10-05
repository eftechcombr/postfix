[![Docker build](https://github.com/eftechcombr/postfix/actions/workflows/build-and-publish.yml/badge.svg)](https://github.com/eftechcombr/postfix/actions/workflows/build-and-publish.yml)


# Postfix SMTP Relay container

Simple postfix smtp to use as relayhost to gmail, mailgun and more. 

<br>

## Docker run

    docker run --rm -d --name postfix \
    -e RELAY_USER=postmaster@domain \
    -e RELAY_PASS=xxxxxxxxx \
    -e RELAY_HOST=smtp.mailgun.org \
    -e RELAY_PORT=587 \
    eftechcombr/postfix:latest

## docker-compose.yaml

    version: '3.2'
    services:
      relay:
        image: eftechcombr/postfix:latest
        restart: unless-stopped
        volumes: 
         - postfix-volume:/var/spool/postfix
        ports:
         - "30025:25"
        env_file: ./.env
    volumes:
      postfix-volume:



 # testing

    
    echo "Email Test" | mail -s "This is a simple test" contato@example.com
 
or

    sendmail -f sender@example.com recipient@example.com
    From: Sender Name <sender@example.com>
    Subject: Amazon SES Test                
    This message was sent using Amazon SES.                
    .




Use https://www.mail-tester.com tool for debug


