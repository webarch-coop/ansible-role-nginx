# Webarchitects Ansible Nginx role 

[![pipeline status](https://git.coop/webarch/nginx/badges/master/pipeline.svg)](https://git.coop/webarch/nginx/-/commits/master)

An Ansible role for installing [Nginx](https://nginx.org/en/) on Debian servers.

## Usage

To only install packages you can run this role using the `nginx_install` tag.

Once Nginx is installed you can use the `nginx_conf` tag with `--check`.


## Defaults

The [default variables](defaults/main.yml):

| Variable name                | Default value                                                                                                                                                                                                                      | Comment                                          |
|------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| `nginx_cipher_suites_tls1_1` | `DHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES256-SHA256:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:DES-CBC3-SHA`                                                                                                                                              | TLSv1 cipher suites                             |
| `nginx_cipher_suites_tls1_2` | `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384` | TLSv2 cipher suites                             |
| `nginx_cipher_suites_tls1_3` | `TLS_AES_128_GCM_SHA256:TLS_AES_256_GCM_SHA384:TLS_CHACHA20_POLY1305_SHA256`                                                                                                                                                        | TLSv3 cipher suites                             |
| `nginx_default_root`         | `/var/www/html`                                                                                                                                                                                                                     | The default document root                       |
| `nginx_dhparam_path`         | `/etc/nginx/ssl_dhparam.pem`                                                                                                                                                                                                        | The path for the dhparam file                   |
| `nginx_dhparam_size`         | `4096`                                                                                                                                                                                                                              | The dhparam size                                |
| `nginx_packages`             | `nginx-extras`                                                                                                                                                                                                                      | A list of `.deb` packages                       |
| `nginx_sites_disabled`       | `[]`                                                                                                                                                                                                                                | Symlinks absent from `/etc/nginx/sites-enabled` |
| `nginx_sites_enabled`        | `default.conf`, `localhost.conf`                                                                                                                                                                                                    | Symlinks present in `/etc/nginx/sites-enabled`  |
| `nginx_tls1_1`               | `false`                                                                                                                                                                                                                             | Enable TLSv1                                    |
| `nginx_tls1_3`               | `true`                                                                                                                                                                                                                              | Enable TLSv3                                    |

