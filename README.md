# node-red-within-express #

This repository contains an HTTP server based on [Node.js](https://nodejs.org/en/) with [Express.js](http://expressjs.com/) including an embedded [Node-RED](https://nodered.org/) instance.

Its intended purpose is to provide a very easily maintainable server for development and test of web and REST service prototypes.

## Features ##

The implemented server has the following features:

* **HTTPS with optional HTTP-to-HTTPS Redirection**<br>the main server handles HTTPS only as it is becoming increasingly difficult to deliver pure HTTP content to browsers (even locally). If desired, an additional auxiliary HTTP server may be started which redirects incoming requests to its HTTPS counterpart
* **Proxy Support**<br>the server can also be used behind proxies
* **Support for "self-signed" or "Let's Encrypt" Certificates**<br>for local tests, it may be sufficient to generate self-signed certificates (instructions can be found below). For public tests, the server also supports certificates generated by ["Let's Encrypt"](https://letsencrypt.org/)
* **Support for "virtual Hosts" and Subdomains**<br>the server may optionally support "virtual hosts" and serve multiple domains (including subdomains) simultaneously. In this case, each domain will be mapped to an individual subtree on the file system in order to isolate the domains from each other
* **"www" Subdomains**<br>if desired, "www" subdomains can be mapped to their original domain (since they usually serve the same content anyway)
* **embedded Node-RED runtime**<br>incoming requests will first be compared to the entry points given by "HTTP in" nodes - and their flows be executed whenever the URL paths match (if "virtual hosts" are to be respected, all these entry points become domain-specific and must therefore be prefixed by the domain they belong to). Requests not matching any "HTTP in" node entry points will then be used to serve static files from the file system (or generate a 404 response if no matching file could be found)
* **embedded Node-RED editor**<br>the embedded Node-RED editor is generally protected by "basic HTTP authentication": the server always comes with a "User Registry" which initially contains a single user (called "node-red" with the initial password "t0pS3cr3t!") who is the only one allowed to access the Node-RED editor
* **User Registry with PBKDF2 hashed Passwords and Role Support**<br>the list of registered users is stored in a JSON file with passwords saved as PBKDF2 hashes with random salt. While the server itself does not contain any user management, it may easily be added as a Node-RED flow - but, in fact, a simple text editor is already sufficient to add new users, change existing ones or remove obsolete users
* **Path-specific CORS**<br>"Cross-Origin Resource Sharing" may be configured for complete sites as a whole or for specific resource paths at any desired granularity
* **configurable "Content Security Policies"**<br>the server is secured using [Helmet](https://github.com/helmetjs/helmet) with a configuration option for specific "Content Security Policies"
* **standard-compliant Logging**<br>access logging is done using [morgan](https://expressjs.com/en/resources/middleware/morgan.html). Logs may be written into a file either in "standard Apache common log format" or any other format

## Installation and Use ##

You may easily install and run this server on your machine.

Just install [NPM](https://docs.npmjs.com/) according to the instructions for your platform and follow these steps:

1. either clone this repository using [git](https://git-scm.com/) or [download a ZIP archive](https://github.com/rozek/node-red-within-express/archive/refs/heads/main.zip) with its contents to your disk and unpack it there 
2. open a shell and navigate to the root directory of this repository
3. run `npm install` in order to install the server

### Preparing the first Start ###

For a quick start, the server comes preconfigured for two different use cases:

* to be run *without* support for virtual hosts<br>this variant does not require much preparation and is ideal for initial experiments
* to be run *with* support for virtual hosts<br>this variant requires a bit of preparational work but may be used to test installations serving multiple domains

#### Variant without Support for virtual Hosts ####

#### Variant with Support for virtual Hosts ####

### First Experiments ###

## Invocation Parameters ##

### Configuring Domains and Virtual Hosts ###

## Embedded Node-RED Instance ##

## User registry ##

### Generating "Salt" and "Hash" ###

## CORS Support ##

## Content Security Polcies ##

## Logging ##



* HTTPS (and auto-redirection from HTTP to HTTPS) with self-signed or "Let's Encrypt" Certificates
* virtual Hosts
  * how to configure Domains in /etc/hosts
  * Subdomains
* User Registry
  * Basic Auth and PBKDF2
  * adding Users to the Registry
  * protecting the Node-RED Editor
* CORS Support
* initial Node-RED Flows
* Postman Collection for Tests


## License ##

[MIT License](LICENSE.md)
