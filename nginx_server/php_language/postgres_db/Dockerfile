FROM php:8.1-fpm

# Install dependencies
RUN apt-get update && apt-get install -y \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    libzip-dev \
    libpq-dev

# Install PHP extensions
RUN docker-php-ext-install soap \
    && docker-php-ext-install zip \
    && docker-php-ext-install sockets \
    && docker-php-ext-install gd \
    && docker-php-ext-install pdo_pgsql pgsql

# Install PHP 8.1 CLI and Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set working directory
WORKDIR /var/www

# Expose port
EXPOSE 9000

# Start PHP-FPM
CMD ["php-fpm"]
