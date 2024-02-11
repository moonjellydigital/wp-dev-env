# WP Dev Env

WP Dev Env is a containerized WordPress development environment. It can be used
with Docker Compose, Docker Stack, and Podman Compose. It's compatible with
arm64/aarch64 Linux.

## Features

* Latest version of WordPress by default, or set your own tag

* Adminer to interact with the database through a web UI

* Pre-install plugins and themes

* Easily change PHP memory limit and max upload size

* WordPress constants set for local development

## Usage

1. (optional) Change WordPress constants in the `docker-compose.yml` file.
See the [documentation for the official WordPress Docker image](https://hub.docker.com/_/wordpress) for more
information about setting constants in `wp-config.php`.

2. (optional) Make a `.env` file to set your own environment variables
instead of using the defaults. Available variables are documented in the
Environment Variables section.

3. (optional) Edit the `upload.ini` file to change the memory limit and
max upload size.

4. (optional) Pre-install plugins or themes by adding the files to the
`plugins` or `themes` directories, respectively. Make sure the files have
read, write, execute permissionsi set for the user.

5. Launch the network. For Docker Compose: `docker-compose up`. for Docker
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

## WordPress Constants

Constant | Value | Note
-------- | ----- | ----
`WP_DEBUG` | 1 | Debug on, messages displayed
`WP_DISABLE_FATAL_ERROR_HANDLER` | true | Displays the error and stack trace instead of the "Check your email..." message.
`SCRIPT_DEBUG` | true | Use development versions of CSS and JavaScript. Necessary for debugging and profiling in React.
`WP_ENVIRONMENT_TYPE` | 'development' | See [WordPress Environment Types](https://make.wordpress.org/core/2020/08/27/wordpress-environment-types/) for more information
`WP_DEVELOPMENT_MODE` | 'all' | Works for both plugin and theme development. See [Configuring Development Mode](https://make.wordpress.org/core/2023/07/14/configuring-development-mode-in-6-3/) for more information.

## Security

This stack is only meant for local development. It shouldn't be open to
the internet. The environment variables for the database default to unsafe
values.

## Troubleshooting & FAQ

<details>
    <summary>When I make a new WordPress I'm getting an old version of WordPress/Adminer/PHP?</summary>
    This happens because Docker caches the images you download. To get a fresh version of an image run
    `docker pull <image name>:<tag>`.

    For example, to get the newest version of the WordPress image with the `latest` tag you would run
    `docker pull wordpress:latest`.
</details>

<details>
    <summary>How do I change the PHP version for WordPress if it's already running?</summary>
    **If you're using the `wordpress:latest` image**, download the newest version
    from Docker Hub by running `docker pull wordpress:latest`. Then run `docker-compose up -d`.
    The WordPress container will be recreated.

    **If you set a particular tag in a `.env` file**, change the tag in the `.env`.
    Then run `docker-compose up -d`. The WordPress container will be recreated.
</details>

## Docker Images

The following images are used in this Docker Compose:

* [WordPress Official Image](https://hub.docker.com/_/wordpress) 

* [MariaDB Official Image](https://hub.docker.com/_/mariadb) 

* [Adminer Official Image](https://hub.docker.com/_/adminer)

## License

It's the user's responsibility to ensure the licensing for the software
contained in the images used in this stack is suitable for their
purposes.
