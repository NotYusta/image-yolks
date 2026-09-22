# image-yolks

Shared container images used as installation bases and runtime foundations for
Pterodactyl / Pelican eggs.

Images are published to `ghcr.io/notyusta/image-yolks`.

## Available Images

### [MySQL](/mysql)

  * [`MySQL 8.4`](/mysql)
    * `ghcr.io/notyusta/image-yolks:mysql_8.4`
  * [`MySQL 9.7`](/mysql)
    * `ghcr.io/notyusta/image-yolks:mysql_9.7`

Ubuntu 24.04 base with the Oracle MySQL APT repository configured and a full
MySQL server + client install. The version is selected at build time with the
`MYSQL_VERSION` build argument. Runnable as a Pterodactyl installation image, a
standalone database, or as the base for the MySQL runtime yolks.

> **Note:** Oracle's MySQL APT repository only publishes `amd64` packages, so
> these images are built for `linux/amd64` only.
