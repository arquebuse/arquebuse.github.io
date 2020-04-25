---
layout: default
title: Setup guide
nav_order: 2
---

For an easy setup, we publish prebuilt Docker images on [Docker Hub](https://hub.docker.com/r/arquebuse/arquebuse).
 
After [installing Docker on your system](https://docs.docker.com/get-docker/), just pull the last version of Arquebuse:
 
    docker pull arquebuse/arquebuse
    
Then, run the container with http port mapping:
 
    docker run -p 443:443 arquebuse/arquebuse
 
You'll be able to connect to the web UI with [https://localhost](https://localhost) or with your system's IP address. Note: your browser will reject the default self-signed SSL certificate. Take a look at the documentation to see how to use a custom (and valid) SSL certificate.  
 
Default credentials are **arquebuse**/**arquebuse** (you are strongly encouraged to change it).
 
To allow Arquebuse to receive emails from other computers add a mapping to Arquebuse internal SMTP server:

    docker run -p 443:443 -p 2525:2525 arquebuse/arquebuse
    
You can now send emails to Arquebuse using your system's IP address and port 2525. You can also use the standard SMTP port 25 while using argument *-p 25:2525*.

Note: it may be a bad idea to expose Arquebuse SMTP port directly on Internet as it's not designed to be bullet proof SMTP server. BTW, Arquebuse doesn't relay emails, it only stores received data into json files...
