# Base image
FROM php:8.1-fpm

# Install dependencies
RUN apt-get update && apt-get install -y \
    curl \
    libzip-dev \
    libpq-dev

# Install PHP extensions
RUN docker-php-ext-install zip pdo_pgsql pgsql

# Install PHP 8.1 CLI and Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Optimize Composer installation
RUN COMPOSER_HOME=/tmp/composer composer --version

# Redis PHP extension
RUN pecl install redis && docker-php-ext-enable redis

# Set working directory
WORKDIR /var/www

# Expose port
EXPOSE 9000

# Start PHP-FPM
CMD ["php-fpm"]
