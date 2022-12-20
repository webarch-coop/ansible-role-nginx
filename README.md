# Webarchitects Ansible Nginx role 

[![pipeline status](https://git.coop/webarch/nginx/badges/master/pipeline.svg)](https://git.coop/webarch/nginx/-/commits/master)

An Ansible role for installing [Nginx](https://nginx.org/en/) on Debian servers.

## Usage

To only install packages you can run this role using the `nginx_install` tag.

Once Nginx is installed you can use the `nginx_conf` tag with `--check`.

## Defaults

The [default variables](defaults/main.yml):

### nginx

If `nginx` is `true` then the tasks in this role will be run, it defaults to `false`.

### nginx_cipher_suites_tls1_2

A list of TLSv1.2 cipher suites, this defaults to the [Mozilla intermediate compatibility list](https://wiki.mozilla.org/Security/Server_Side_TLS#Intermediate_compatibility_.28recommended.29).

`ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384`

### nginx_cipher_suites_tls1_3

A list of TLSv1.2 cipher suites, this defaults to the [Mozilla modern compatibility list](https://wiki.mozilla.org/Security/Server_Side_TLS#Modern_compatibility).

`TLS_AES_128_GCM_SHA256:TLS_AES_256_GCM_SHA384:TLS_CHACHA20_POLY1305_SHA256`

### nginx_default_https_redirect

A URL to redirect HTTP requests to, `nginx_default_https_redirect` defaults to `https://$host$request_uri`.

### nginx_default_redirect

An optional URL to redirect port 443 requests to the `nginx_default_server_name` to. This variable is not set by default.

### nginx_default_root

The default `root` for HTML files, this defaults to `/var/www/html`.

### nginx_default_server

If `nginx_default_server` is `true` then the `default.conf` server configuration will include `default_server` in the `listen` directive, it defaults to `true`.

### nginx_default_server_index

A list of file names to be used for the `index` directive, it defaults to:

* `index.html`
* `index.nginx-debian.html`

### nginx_default_server_name

The `server_name` to use in the `default.conf` server configuration, it defaults to `{{ inventory_hostname }}`.

### nginx_default_ssl_certificate

An optional path to a TLS certificate for the `default.conf` server configuration, set it to an empty string to disable TLS in `default.conf`.

### nginx_default_ssl_certificate_key

An optional path to a TLS key for the `default.conf` server configuration, set it to an empty string to disable TLS in `default.conf`.

### nginx_default_ssl_trusted_certificate

An optional path to a CA certificate for the `default.conf` server configuration, set it to an empty string to disable TLS in `default.conf`.

### nginx_dhparam_path

The path to the Diffie-Hellman parameters TLS key, this defaults to `/etc/nginx/ssl_dhparam.pem`.

### nginx_dhparam_size

The size of the Diffie-Hellman parameters TLS key, this defaults to `4096` (smaller ones are quicker to generate).

### nginx_packages

A list of Debian package to be installed by this role, this defaults to:

* `nginx-extras`

### nginx_sites_disabled

A list of symlinks in `/etc/nginx/sites-enabled` to delete, this defaults to:

* `default`

### nginx_sites_enabled

A list of files that are present in `/etc/nginx/sites-available` that should be symlinked from `/etc/nginx/sites-enabled`, this defaults to:

* `default.conf`
* `localhost.conf`

## nginx_ssl_protocols

A list of TLS protocols for [ssl_protocols](https://nginx.org/en/docs/http/ngx_http_ssl_module.html#ssl_protocols), this defaults to:

* `TLSv1.2`
* `TLSv1.3`

This role no loger supports `TLSv1.1` or `TLSv1.0`.
