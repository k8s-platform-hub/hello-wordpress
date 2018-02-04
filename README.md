# hello-wordpress

git push and deploy a Wordpress website with free HTTPS domain.

This project is a Wordpress installation with MySQL which can be deployed to the cloud using Hasura's free hosting tier. Immediately get a HTTPS domain and access to Wordpress admin dashboard. Custom domain can be deployed with simple `git push` and HTTPS is added automatically.

## What's included?

- Wordpress website with free HTTPS domain
- MySQL database

## Quickstart

```bash
# quickstart from this project
$ hasura quickstart hello-wordpress
$ cd hello-wordpress
```

The quickstart command does the following:

- Creates a new directory `hello-wordpress` in the current working directory
- Creates a free Hasura cluster and sets it as the default for this project
- Sets up a git repository and adds hasura remote to push code
- Adds your SSH public key to the cluster so that you can push to it

### Set MySQL password

```bash

# set a password for mysql database
$ hasura secrets update mysql.password [secure-password]
# verify the password
$ hasura secrets list

```

### Deploy

```bash
# git push to deploy
$ git add . && git commit -m "First commit"
$ git push hasura master
```

Once deployed, access the website using the following command:

```bash
# open wordpress website in a browser
$ hasura microservice open wordpress
```

## Viewing server logs

```bash
# see status of microservices
$ hasura microservice list

# get logs for wordpress
$ hasura microservice logs wordpress
```

## Adding a custom domain

A custom domain can be added in 3 easy steps. Hasura provides free SSL certificates using [LetsEncrypt](https://letsencrypt.org/).

Checkout [Custom domains & SSL on Hasura Docs](https://docs.hasura.io/0.15/manual/gateway/custom-domains-ssl.html) for complete instructions.

## Accessing files on the cluster

To get a shell inside Wordpress microservice, use [hasura microservice exec](https://docs.hasura.io/0.15/manual/hasuractl/hasura_microservice_exec.html):

```bash
$ hasura microservice exec -it wordpress -- bash
root@wordpress-2112168164-p91qj:/var/www/html#
```

To copy files to and from the microservice, use [hasura microservice copy](https://docs.hasura.io/0.15/manual/hasuractl/hasura_microservice_cp.html):

```bash
# copy wp-config.php from the microservice to your system:
$ hasura ms cp wordpress:/var/www/html/wp-config.php wp-config.php

# copy wp-config.php from your system to the microservice:
$ hasura ms cp wp-config.php wordpress:/var/www/html/wp-config.php
```
