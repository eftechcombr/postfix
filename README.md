# postfix

## Images

 - [x] eftechcombr/postfix:latest
 - [x] eftechcombr/postfix:mailgun
 - [x] eftechcombr/postfix:mailgun-europe
 - [x] eftechcombr/postfix:ses
 - [x] eftechcombr/postfix:gmail
 - [x] eftechcombr/postfix:office365
 - [x] eftechcombr/postfix:sendgrid
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
    #
    ### Services
    #
    services:
    #
    # MAILGUN
    #
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
         
    #
    ### Volumes
    #
    volumes:
      postfix-volume:
      
      

 # testing

    echo "Email Test" | mail -s "This is a simple test" contato@eftechcombr.com.br
 
or

    sendmail -f sender@example.com recipient@example.com
    From: Sender Name <sender@example.com>
    Subject: Amazon SES Test                
    This message was sent using Amazon SES.                
    .




