---
title: Build Your Site or Blog with Docker, Traefik, and Ghost
show_author_profile: true
tags: Docker Traefik Ghost Linux
article_header:
  type: cover
  image:
    src: /assets/images/containers-stacked-unsplash.jpg
---

## Introduction and Goals for this Project  

Whenever I update my personal site, I always try to incorporate new apps and technologies that I am interested in learning about. I've been using [Docker](https://www.docker.com/) on my home network for a while and it has really changed my approach to building servers. Docker containers are fast and lightweight. Even better, they are a breeze to administer and allow you to do some interesting thing with networking and encryption.

[Traefik](https://traefik.io/) is a lightweight http proxy that works great with Docker. It uses Docker labels to direct traffic between hosts and ports. That means that we can send all port 80 and 443 traffic for any number of domains into Traefik and then direct it to various Docker containers running on the same host. Because all traffic goes through the Traefik proxy container, we don't need to expose the other containers to the Internet.

Traefik is integrated with [Let's Encrypt](https://letsencrypt.org/) for [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security) encryption. Let's Encrypt is a free, automated, and open certificate authority that is run by a non-profit. I've been using it with my favorite http/2 web server ([Caddy](https://caddyserver.com/)) for a while, but for this project I am going in a different direction. The great thing about Traefik's Let's Encrypt integration is that handles your certificate requests automatically for any domains you add to your Traefik proxy. By configuring Traefik to handle your certificates, there's no need to worry about enabling encryption on any of your other containers. That will be very convenient if you ever decide to change blogging software or somehow corrupt some part of your software stack. Just point Traefik at the new container and you are back up and running. Part of the magic of Docker is being able to destroy your existing container without losing any of the configuration files because they are stored in your host file system. When you recreate your container, you can just point it at the same configuration files and host directories.

I wanted to try [Ghost](https://ghost.org/) as the front-end sofware for this site because it seems to be lightweight and relatively easy to modify. I don't like to design web sites anymore, so I wanted something that had a lot of themes to choose from. I also wanted something that wouldn't get in my way when I felt like posting. So far, Ghost is up to the task. I'll talk about adding Ghost into the mix in another post.

## Operating System

I'm using CentOS 7 x64 on a [Vultr](https://www.vultr.com/?ref=7091040) VPS with Selinux disabled. There's no real advantage to using any particular host OS, so use whataver you like. These steps are geared towards linux, so they might not work for a Windows host system.

## Domain Names

In order to follow along, you'll need an A record pointing at your IP and a CNAME pointing at your domain for the "monitor" subdomain. You can set these records at the place where you manage your DNS.

[Go to Part 2](2018-01-06-installing-docker-on-centos.html): Installing Docker on CentOS

[Go to Part 3](2018-01-07-install-and-configure-traefik-in-docker.html): Install and Configure Traefik
