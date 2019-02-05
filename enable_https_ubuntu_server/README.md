# Enable HTTPS on Ubuntu 18.04

## Overview

The main server that serves the domain cet.ac.in and other related domains runs
on Ubuntu 18.04.

An instance of Nginx is used to handle all the requests to the server on the
ports 80 and 443 (80 and 443 are the default ports a web browser attempts to
connect for an http request and an https request respectively).

Static files are to be directly served by the Nginx service to improve latency.

An instance of Apache Web Server is used to serve services programmed in PHP
(PHP: Hypertext Preprocessor).

NodeJS services are spawned and managed using pm2.

### Nginx

* Listens on port 80 and 443.

#### Configuration of Nginx available in the directory:

`/etc/nginx/`

#### Configuration of sites in directory:

`/etc/nginx/sites-available/`

#### To enable a site:

`ln -s /etc/nginx/sites-available/new_site /etc/nginx/sites-enabled/new_site`

#### To disable a site:

Remove symlink from `/etc/nginx/sites-enabled/`

#### To ensure the configuration files of Nginx is correct and loadable, execute:

`nginx -t`

### Apache Web Server

* Listens on port 8000 and 8002.

#### Configuration of Apache Web Server available in the directory:

`/etc/apache2/`

#### Configuration of sites in directory:

`/etc/apache2/sites-available/`

#### To enable a site:

`a2ensite new-site.conf`

#### To disable a site:

`a2dissite new-site.conf`

#### To ensure the configuration files of Apache is correct and loadable, execute:

`apachectl -t`

## Enabling HTTPS

We rely on Let's Encrypt free, automated, and open Certificate Authority for
generating certificate to support HTTPS communication.

See https://letsencrypt.org/ .

Certbot(https://certbot.eff.org/) is used to automatically enable HTTPS on your website with EFF's Certbot, deploying Let's Encrypt certificates.

Certbot is already installed for our server.

### Execution
 Execute
`letsencrypt`
with root permissions.

Certbot is interactive and will guide through the steps necessary for deployment.

#### Note

It is to be noted that the certificate is deployed for the websites served through 80 and 443(Nginx). ie the communication between the client browser/service and Nginx is encrypted. Nothing else(assuming security and safety of internal port communications).

In some cases, there may arise a situation where communication between Nginx and other services need to be encrypted for various reasons. If such a scenario arises, configuration of Nginx and the respective service needs to be configured to use a locally generated certificate to enable https communication between the two.
