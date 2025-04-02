# Project Setup and Management

This project uses Docker and Docker Compose to manage the development environment. The `Makefile` provides a set of commands to build, start, stop, and manage the Docker containers.

It's designed to be used with a PHP application (with composer) and includes a MySQL database (MariaDB) and RabbitMQ for message queuing.

## Prerequisites

- Docker
- Docker Compose
- Make
- awk
- gawk

## Commands

### `make all`

This command is a placeholder and does not perform any actions. It is included for completeness.

### `make pre-up`

Displays the current user ID, group ID, and target architecture.

### `make build`

Builds the Docker images with the appropriate architecture.

### `make up`

Runs the `pre-up` and `build` commands, then starts the Docker containers in detached mode.

### `make down`

Stops and removes the Docker containers, volumes, and images.

### `make stop`

Stops the Docker containers without removing them.

### `make status`

Displays the status of the Docker containers.

### `make setup`

Starts the Docker containers, Builds the images with the appropriate architecture, and installs Composer dependencies.

## Usage

1. **Build and start the containers:**

   ```sh
   make up
    ```
   
2. **Stop and remove the containers, volumes, and images:**

    ```sh
    make down
    ```
   
3. **Stop the containers without removing them:**

    ```sh
    make stop
    ```
   
4. **Display the status of the containers:**

    ```sh
    make status
    ```
   
5. **Set up the project by installing Composer dependencies:**

    ```sh
    make setup
    ```
   
6. **Display the current user ID, group ID, and target architecture:**

    ```sh
    make pre-up
    ```
   
7. **Build the Docker images:**

    ```sh
    make build
    ```

## Nginx

Will serve the files from the `public` directory of the application.

The Nginx configuration file is set up to handle PHP requests.

## RabbitMQ

The RabbitMQ service is included in the Docker Compose file. It is used for message queuing and can be configured as needed.

## PHP

The PHP service is set up to run the application. It uses the `php:8.2-fpm` image and includes the necessary extensions for the application.

## MySQL

The MySQL service is set up to use the `mariadb:latest` image.

## DB Autoload

The `db` directory is used to load the database schema and data when the MySQL container is started.

- The `.sql` file is used to create the database schema.

## Docker Compose

The `docker-compose.yml` file defines the services, networks, and volumes used in the project.

Can be used to start the application and database containers + rabbitmq (can be commented or adapted to other messaging queues if needed).

## Dockerfile

The `Dockerfile` is used to build the Docker images for the application. It includes the following steps:
- Set the base image to `php:8.2-fpm`.
- Install required packages and extensions.
- Set the working directory to `/var/www/`.
- Composer is installed and dependencies are installed.

Provided Composer file is only as a placeholder, you can adapt it to your needs.


## Notes

- Ensure that Docker and Docker Compose are installed and running on your system.
- The `CURRENT_UID` and `CURRENT_GID` environment variables are used to set the file ownership inside the Docker containers to match the host user.