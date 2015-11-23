---
title: Exploring go template
---

In this assignment, you'll learn basic of go template syntax and play for fun!

## Background

[Golang](https://golang.org/) is a new language for writing concurrent systems. Since all of you satisfy [prerequisites](https://github.com/mulab/OMG-resources#prerequisites), you'll have no trouble accessing golang resources. Today we are going to learn about golang's temmplate syntax, since that would
be helpful if you're writing a system based on golang and providing a web interface.

## Pre-Assignment

This assignment is a warm-up assignment and can be done with the following steps:

0. Install go if you don't have one.
- Install github.com/cgcgbcbc/gorender.
- Read documents for [text/template](https://golang.org/pkg/text/template/) (require), [html/template](https://golang.org/pkg/html/template/) (optional)
- Write some simple template file and render them with gorender, watch the result.

## Assignment

In Lab μ, we use consul for service discovery. Currently, our global reverse proxy (nginx) uses dns interface of consul to lookup services. For example, wordpress.service.lab.mu is the internal hostname for our blog(currently down). But due to nginx's dns cache, if we restart our blog container, its IP address
changed, but the hostname in the nginx container still points to the old IP address, which would cause trouble and we have to restart our whole web services.
A more flexible solution is to use consul-template, which subscribe consul notifications and render template files.

This assignment can be done with the following steps:

0. Read the documents of [consul](https://consul.io/)
- Install consul in your local machine.
- Read the documents of [registrator](https://github.com/gliderlabs/registrator)
- Install registrator and get consul and registrator work together.
- Read the documents of [consul-template](https://github.com/hashicorp/consul-template)
- Write a template that will render nginx configurations from consul services.

example config:
```
upstream labmu_website {
        server globalproxy_labmuwebsite-80.service.lab.mu;
}
server {
        listen 80 default;
        gzip on;
        gzip_comp_level 4;
        gzip_types application/javascript text/css image/svg+xml;
        server_name www.lab.mu lab.mu;
        access_log /var/log/nginx/labmu_website.access;
        error_log /var/log/nginx/labmu_website.error;
        location / {
                proxy_pass http://labmu_website;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
        }
}

```

Since this assignment may be a bit more difficult for starters, we can hold up a discussion session from week to week if you require.

## Submission

Fork this repo, add the template file named with `[your github id].tmpl` in this folder and open a pull request.

## Discussion

It seems that if a service is restarted, simply reload nginx will make all things right. The only problem remains is that when we restart
the host, nginx will fail to start since some of the sites'upstream domain are not available. So the simplest solution may be: dynamic add conf to sites-enable when container starts and remove conf when container stops.
