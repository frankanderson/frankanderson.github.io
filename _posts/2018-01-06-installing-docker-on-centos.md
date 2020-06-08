---
title: Installing Docker on CentOS
tags: Docker Traefik Ghost Linux CentOS
article_header:
  type: cover
  image:
    src: /assets/images/containers-stacked-unsplash.jpg
sidebar:
  nav: traefik1
---

## Part 2 of [Build Your Site or Blog on Docker, Traefik, & Ghost](2018-01-05-build-your-site-on-docker-traefik-ghost.md)

Using the appropriate package manager for your distro, update your software and install Docker:

`# yum update`

`# yum install docker device-mapper-libs device-mapper-event-libs`

Start Docker:

`# systemctl start docker.service`

Enable the Docker server so that it will restart after a reboot:

`# systemctl enable docker.service`

Now you can test your install:

_Note: Docker needs elevated privileges to work correctly. Figuring out the best way to reduce your attack surface is beyond the scope of this article, but it is a best practice to run containers as a limited user, not root. From this point on, assume that all docker commands are using sudo or an account with elevated priveleges._

`# docker run hello-world`

Assuming you didn't see any errors, you are ready to install Docker Compose:
    

```
# sudo curl -L https://github.com/docker/compose/releases/download/1.17.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

_Note: Use the latest Compose release number (e.g., 1.17.1) in the download command._

_The above command is an example, and it is probably out-of-date. To ensure you have the latest version, check the [Docker Compose repository release page on GitHub](https://github.com/docker/compose/releases)._

Apply executable permissions to the binary:

`# sudo chmod +x /usr/local/bin/docker-compose`

Test Docker Compose:

```
# docker-compose -v
docker-compose version 1.17.1, build 6d101fb
```
