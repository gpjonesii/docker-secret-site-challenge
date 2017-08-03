## Synopsis

This repo contains the results of the following challenge:

```
I need a small web app (a single HTML page) to be available online. The webpage content is 
confidential so I need it to be secured with Basic authentication over TLS.  I also would like to 
support a secret token within the URL as a second authentication factor.  I would like all the 
security verification to take place in a separate container before reaching the container that 
hosts the confidential content.  I need to be able to build the entire solution from Dockerfiles and 
deploy it via Docker Compose. 
 
The credentials that should work are: admin : Password1 
The content should be available at https://<host:port>/uj47G/index.htm 
```

## Repository Contents

```
[gjones@brooklyn]~/src/secretstatic% tree                                                 
.
├── docker-compose.yml     <### Docker Compose yaml - instructs docker-compose on what to build, ports to expose, commands to run, etc.
├── proxy        <### our proxy directory
│   ├── certs      <### Normally, we wouldn't want to store certificates in SCM, *specifically* server keys, but this is a simple challenge project
│   │   ├── server.crt
│   │   ├── server.csr
│   │   ├── server.key
│   │   └── server.pem
│   ├── Dockerfile  <### our dockerfile that instructs docker how to build our haproxy container image
│   ├── haproxy.cfg <### This is where all of the authentication, acl, and rewriting magic happens - our haproxy config file
│   ├── haproxy_start.sh <### this is a wrapper shell script for haproxy - it is copied into and set as the default command of the resultant container image
│   └── no-access.htm <### Just a dumb html doc that is returned if a URI is used that doesn't include our super secret, security-through-obscurity, URI token
├── README.md <### you're reading it!
└── web  <### Our web directory
    ├── conf  <### This directory contains all of our nginx configs - at the moment, only nginx.conf, but any file in this dir will land in /etc/nginx/ in the container image
    │   └── nginx.conf
    ├── content <### This is our website content. Currently, just a simple index.htm file
    │   └── index.htm
    └── Dockerfile <### our dockerfile that instructs docker how to build our we container image

5 directories, 13 files
```

## Running 


`docker-compose build`
`docker-compose up`

