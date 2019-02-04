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

# Nginx
