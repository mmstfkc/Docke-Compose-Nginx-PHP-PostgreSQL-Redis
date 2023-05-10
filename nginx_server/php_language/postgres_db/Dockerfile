# Base image
FROM php:8.1-fpm

# Install dependencies
RUN apt-get update && apt-get install -y \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    libzip-dev \
    libpq-dev \
    nginx \
    net-tools \
    iputils-ping \
    libxml2 \
    libxml2-dev \
    libssl-dev \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libpq-dev \
    libssl-dev \
    libcurl4-openssl-dev \
    libonig-dev \
    libmcrypt-dev \
    libreadline-dev

# Install PHP extensions
RUN docker-php-ext-install soap \
    && docker-php-ext-install zip \
    && docker-php-ext-install sockets \
    && docker-php-ext-install gd

# Install PHP 8.1 CLI and Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install PostgreSQL client
RUN apt-get install -y postgresql-client

# Install pdo_pgsql and pgsql extensions manually
RUN docker-php-source extract \
    && docker-php-ext-install pdo_pgsql pgsql \
    && docker-php-source delete

# Install Redis extension
RUN pecl install redis \
    && docker-php-ext-enable redis

# Set working directory
WORKDIR /var/www

# Configure nginx
COPY ./nginx/sites-enabled/ /etc/nginx/conf.d/

# Expose ports
EXPOSE 80

# Start nginx and PHP-FPM
CMD service nginx start && php-fpm -F
