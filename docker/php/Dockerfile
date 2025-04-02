# Use the official PHP image as a base
FROM php:8.2-fpm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libzip-dev \
    mariadb-client

# Install PHP extensions
RUN docker-php-ext-install zip pdo_mysql sockets

# Set working directory
WORKDIR /var/www

# Copy the Composer binary from the official Composer image
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Copy the application files
COPY . /var/www

# Set the user and group ID for file ownership
ARG UID
ARG GID
RUN chown -R ${UID}:${GID} /var/www

# Switch to the current user
USER ${UID}:${GID}

# Install Composer dependencies
RUN composer install --working-dir=/var/www

# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]