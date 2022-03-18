# WP Dev Env

**WARNING: At this point, anything could change at any future commit.**

WP Dev Env is an arm64 architecture compatible containerized WordPress
development environment. It can be used with Docker Compose, Docker Stack,
and Podman Compose.

## Features

* Latest version of WordPress

* Adminer to interact with the database through a web UI

* Pre-install plugins and themes

* Easily change PHP memory limit and max upload size

* Debug mode is enabled

## Usage

1. Change the following environment variables in `docker-compose.yml` to
suit your requirements: `MYSQL_DATABASE`, `MYSQL_USER`, `MYSQL_PASSWORD`,
`WORDPRESS_DB_USER`, `WORDPRESS_DB_PASSWORD`, and `WORDPRESS_DB_NAME`.

2. (optional) Change the `WORDPRESS_TABLE_PREFIX` environment variable.

3. (optional) Change the port mappings in `docker-compose.yml`. For example
to make the WordPress site available on localhost:4000 change the ports
entry for the `web` service from `8080:80` to `4000:80`. The host
machine port is to the left of the colon and the container's port is to
the right.

4. (optional) Edit the `upload.ini` file to change the memory limit and
max upload size.

5. (optional) Pre-install plugins or themes by adding the files to the
`plugins` or `themes` directories, respectively. Make sure the files have
read, write, execute permissionsi set for the user.

6. Launch the network. For Docker Compose: `docker-compose up`. for Docker
Stack: `docker stack deploy`, for Podman Compose: `podman-compose up`.

## License

It's the user's responsibility to ensure the licensing for the software
contained in the images used in this stack are suitable for their
purposes.
