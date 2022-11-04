# WP Dev Env

WP Dev Env is an arm64 architecture compatible containerized WordPress
development environment. It can be used with Docker Compose, Docker Stack,
and Podman Compose.

## Features

* Latest version of WordPress by default, or set your own tag

* Adminer to interact with the database through a web UI

* Pre-install plugins and themes

* Easily change PHP memory limit and max upload size

* Debug mode is enabled

## Usage

1. (optional) Make a `.env` file to set your own environment variables
instead of using the defaults. Available variables are documented in the
Environment Variables section.

2. (optional) Edit the `upload.ini` file to change the memory limit and
max upload size.

3. (optional) Pre-install plugins or themes by adding the files to the
`plugins` or `themes` directories, respectively. Make sure the files have
read, write, execute permissionsi set for the user.

4. Launch the network. For Docker Compose: `docker-compose up`. for Docker
Stack: `docker stack deploy`, for Podman Compose: `podman-compose up`.

## Environment Variables

Variable | Default | Description
-------- | ------- | -----------
`WPDB_NAME` | exampledb | Name of the database WordPress should use
`WPDB_USER` | exampleuser | Database user's username
`WPDB_PASS` | examplepass | Database user's password
`WPDB_TABLE_PREFIX` | wp_ | Database table prefix
`WP_TAG` | latest | Docker tag for the WordPress image
`ADMINER_TAG` | latest | Docker tag for the Adminer image
`MARIADB_TAG` | 10.5 | Docker tag for the MariaDB image
`WP_PORT` | 8080 | Host machine (your computer) port WordPress should use
`ADMINER_PORT` | 8081 | Host machine (your computer) port Adminer should use
`WPDB_PORT` | 6603 | Host machine (your computer) port MariaDB should use

## Docker Images

The following images are used in this Docker Compose:

[WordPress Official Image](https://hub.docker.com/_/wordpress)
[MariaDB Official Image](https://hub.docker.com/_/mariadb)
[Adminer Official Image](https://hub.docker.com/_/adminer)

## License

It's the user's responsibility to ensure the licensing for the software
contained in the images used in this stack are suitable for their
purposes.
