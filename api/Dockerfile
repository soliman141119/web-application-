# Use an official PHP runtime as a parent image
FROM php:8.1.27-apache

# Set the working directory to /var/www/html
WORKDIR /var/www/html

# Copy composer.lock and composer.json to install dependencies
COPY composer.lock composer.json /var/www/html/

# Install any dependencies
RUN apt-get update && \
    apt-get install -y \
        libonig-dev \
        libzip-dev \
        unzip \
        git \
    && docker-php-ext-install pdo_mysql zip

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy the rest of the application code to the working directory
COPY .   /var/www/html/

# Set proper permissions
#RUN  chmod -R 775 /var/www/html/storage

# Expose port 80 and enable Apache's mod_rewrite
EXPOSE 8000
RUN a2enmod rewrite

# Apache configuration
COPY apache.conf /etc/apache2/sites-available/000-default.conf

# Set the 'ServerName' directive to suppress a warning
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

# Start Apache
CMD ["apache2-foreground"]
