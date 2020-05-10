## PHP-ALPINE: Fresh PHP binaries APK repository for Alpine Linux.

 > Maintainer: [@hernandev](https://github.com/hernandev)

This project provides a simple alternative for running updated PHP binaries on Alpine Linux.

We pack and release PHP versions as soon they are available on http://php.net. (At least, we try to.)

Additionally, many PECL extensions are also available as packages as well.

---


## APK Repositories & Release Cycle

<!-- ### PHP End of Support -->
<!-- - **PHP 7.4**     | 2021-11-28   1638057600-->
<!-- PHP 7.3     | 2020-12-06 | 1607212800-->
<!-- Alpine 3.11 | 2021-11-01 | 1635724800-->
<!-- Alpine 3.10 | 2021-05-01 | 1619827200-->
<!-- Alpine 3.9  | 2020-11-01 | 1604188800-->

| Alpine      | PHP                                                                                          |  End of Support  | Repository URL                                                                                |
| -           | -                                                                                            | -                | -                                                                                             |
| ![Alpine 3.11](https://img.shields.io/badge/Alpine-v3.11-blue?style=for-the-badge) | ![PHP 7.4](https://img.shields.io/badge/PHP-7.4-blueviolet?style=for-the-badge) ![](https://img.shields.io/badge/dynamic/json?label=PHP&query=$.latest_version&style=for-the-badge&color=blueviolet&url=https://api.bintray.com/packages/php-alpine/v3.11/php-7.4) | ![EOS](https://img.shields.io/badge/EOS-2021--11--01-success?style=for-the-badge) | [`https://dl.bintray.com/php-alpine/v3.11/php-7.4`](https://dl.bintray.com/php-alpine/v3.11/php-7.4) |
| ![Alpine 3.11](https://img.shields.io/badge/Alpine-v3.11-blue?style=for-the-badge) | ![PHP 7.3](https://img.shields.io/badge/PHP-7.3-blueviolet?style=for-the-badge) ![](https://img.shields.io/badge/dynamic/json?label=PHP&query=$.latest_version&style=for-the-badge&color=blueviolet&url=https://api.bintray.com/packages/php-alpine/v3.11/php-7.3) | ![EOS](https://img.shields.io/badge/EOS-2021--05--01-success?style=for-the-badge) | [`https://dl.bintray.com/php-alpine/v3.11/php-7.3`](https://dl.bintray.com/php-alpine/v3.11/php-7.3) |
| ![Alpine 3.10](https://img.shields.io/badge/Alpine-v3.10-blue?style=for-the-badge) | ![PHP 7.4](https://img.shields.io/badge/PHP-7.4-blueviolet?style=for-the-badge) ![](https://img.shields.io/badge/dynamic/json?label=PHP&query=$.latest_version&style=for-the-badge&color=blueviolet&url=https://api.bintray.com/packages/php-alpine/v3.10/php-7.4) | ![EOS](https://img.shields.io/badge/EOS-2021--11--01-success?style=for-the-badge) | [`https://dl.bintray.com/php-alpine/v3.10/php-7.4`](https://dl.bintray.com/php-alpine/v3.10/php-7.4) |
| ![Alpine 3.10](https://img.shields.io/badge/Alpine-v3.10-blue?style=for-the-badge) | ![PHP 7.3](https://img.shields.io/badge/PHP-7.3-blueviolet?style=for-the-badge) ![](https://img.shields.io/badge/dynamic/json?label=PHP&query=$.latest_version&style=for-the-badge&color=blueviolet&url=https://api.bintray.com/packages/php-alpine/v3.10/php-7.3) | ![EOS](https://img.shields.io/badge/EOS-2020--12--06-success?style=for-the-badge) | [`https://dl.bintray.com/php-alpine/v3.10/php-7.3`](https://dl.bintray.com/php-alpine/v3.10/php-7.3) |
| ![Alpine 3.9](https://img.shields.io/badge/Alpine-v3.9-blue?style=for-the-badge)   | ![PHP 7.4](https://img.shields.io/badge/PHP-7.4-blueviolet?style=for-the-badge) ![](https://img.shields.io/badge/dynamic/json?label=PHP&query=$.latest_version&style=for-the-badge&color=blueviolet&url=https://api.bintray.com/packages/php-alpine/v3.9/php-7.4)  | ![EOS](https://img.shields.io/badge/EOS-2020--11--01-success?style=for-the-badge) | [`https://dl.bintray.com/php-alpine/v3.9/php-7.4`](https://dl.bintray.com/php-alpine/v3.9/php-7.4)   |
| ![Alpine 3.9](https://img.shields.io/badge/Alpine-v3.9-blue?style=for-the-badge)   | ![PHP 7.3](https://img.shields.io/badge/PHP-7.3-blueviolet?style=for-the-badge) ![](https://img.shields.io/badge/dynamic/json?label=PHP&query=$.latest_version&style=for-the-badge&color=blueviolet&url=https://api.bintray.com/packages/php-alpine/v3.9/php-7.3)  | ![EOS](https://img.shields.io/badge/EOS-2020--11--01-success?style=for-the-badge) | [`https://dl.bintray.com/php-alpine/v3.9/php-7.3`](https://dl.bintray.com/php-alpine/v3.9/php-7.3)   |

Builds are available as soon as possible, and EOS is determined by:
- If either PHP or Alpine release reaches end of support, the repository will stop receiving updates.
- Support for both PHP and Alpine are estimated for around 2 years from release date.

Active support reference:

- PHP: https://www.php.net/supported-versions.php
- Alpine: https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases  

> Replace examples below with desired Alpine and PHP versions.


## Snippets

The following code snippets are intended for quick usage on either shell scripts or Dockerfile

> Notice that `main` and `community` official repositories must be enabled.

### Dockerfile

You may skip the ca-certificates part if you replace HTTPS by HTTP but you should not. PHP packages will eventually install ca-certificates anyway.

```dockerfile
FROM alpine:3.11

ADD https://dl.bintray.com/php-alpine/key/php-alpine.rsa.pub /etc/apk/keys/php-alpine.rsa.pub

RUN apk --update add ca-certificates && \
    echo "https://dl.bintray.com/php-alpine/v3.11/php-7.4" >> /etc/apk/repositories

# install php and some extensions
RUN apk add --update \
    php \
    php-bz2 \
    php-json \
    php-mysql \
    php-any-other-available-package... 
```


## Available Packages

This is the complete available packages list:

| Package Name          | Type            |
| -                     | -               |
| `php`                 | PHP Core        |
| `php-common`          | PHP Core        |
| `php-fpm`             | PHP Core        |
| `php-cgi`             | PHP Core        |
| `php-apache2`         | PHP Core        |
| `php-doc`             | PHP Core        |
| `php-dev`             | PHP Core        |
|  -                    |                 |
| `php-sodium`          | Core Extension  |
| `php-bcmath`          | Core Extension  |
| `php-bz2`             | Core Extension  |
| `php-calendar`        | Core Extension  |
| `php-ctype`           | Core Extension  |
| `php-curl`            | Core Extension  |
| `php-dba`             | Core Extension  |
| `php-dom`             | Core Extension  |
| `php-embed`           | Core Extension  |
| `php-enchant`         | Core Extension  |
| `php-exif`            | Core Extension  |
| `php-ftp`             | Core Extension  |
| `php-gd`              | Core Extension  |
| `php-gettext`         | Core Extension  |
| `php-gmp`             | Core Extension  |
| `php-iconv`           | Core Extension  |
| `php-imap`            | Core Extension  |
| `php-intl`            | Core Extension  |
| `php-json`            | Core Extension  |
| `php-ldap`            | Core Extension  |
| `php-litespeed`       | Core Extension  |
| `php-mbstring`        | Core Extension  |
| `php-mcrypt`          | Core Extension  |
| `php-mysqli`          | Core Extension  |
| `php-mysqlnd`         | Core Extension  |
| `php-odbc`            | Core Extension  |
| `php-opcache`         | Core Extension  |
| `php-openssl`         | Core Extension  |
| `php-pcntl`           | Core Extension  |
| `php-pdo`             | Core Extension  |
| `php-pdo_dblib`       | Core Extension  |
| `php-pdo_mysql`       | Core Extension  |
| `php-pdo_pgsql`       | Core Extension  |
| `php-pdo_sqlite`      | Core Extension  |
| `php-pear`            | Core Extension  |
| `php-pgsql`           | Core Extension  |
| `php-phar`            | Core Extension  |
| `php-phpdbg`          | Core Extension  |
| `php-posix`           | Core Extension  |
| `php-pspell`          | Core Extension  |
| `php-session`         | Core Extension  |
| `php-shmop`           | Core Extension  |
| `php-snmp`            | Core Extension  |
| `php-soap`            | Core Extension  |
| `php-sockets`         | Core Extension  |
| `php-sqlite3`         | Core Extension  |
| `php-sysvmsg`         | Core Extension  |
| `php-sysvsem`         | Core Extension  |
| `php-tidy`            | Core Extension  |
| `php-wddx`            | Core Extension  |
| `php-xml`             | Core Extension  |
| `php-xmlreader`       | Core Extension  |
| `php-xmlrpc`          | Core Extension  |
| `php-xsl`             | Core Extension  |
| `php-zip`             | Core Extension  |
| `php-zlib`            | Core Extension  |
|  -                    |                 |
| `php-amqp`            | Extra Extension |
| `php-apcu`            | Extra Extension |
| `php-ast`             | Extra Extension |
| `php-ds`              | Extra Extension |
| `php-imagick`         | Extra Extension |
| `php-mailparse`       | Extra Extension |
| `php-memcached`       | Extra Extension |
| `php-mongodb`         | Extra Extension |
| `php-msgpack`         | Extra Extension |
| `php-psr`             | Extra Extension |
| `php-phalcon`         | Extra Extension |
| `php-redis`           | Extra Extension |
| `php-ssh2`            | Extra Extension |
| `php-swoole`          | Extra Extension |
| `php-timecop`         | Extra Extension |
| `php-libsodium`       | Extra Extension |
| `php-scalar_objects`  | Extra Extension |
| `php-secp256k1`       | Extra Extension |
| `php-xdebug`          | Extra Extension |
|  -                    |                 |
| `argon2`              | Extra Package   |
| `argon2-dev`          | Extra Package   |
| `libargon2`           | Extra Package   |
| `secp256k1`           | Extra Package   |


> Life's good!
