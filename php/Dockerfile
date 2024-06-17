FROM php:8.3-apache

# Update and upgrade packages
RUN apt-get update && apt-get upgrade -y

# Install CodeIgniter 4 dependencies (ext-intl, ext-gd, ext-zip)
# Enable required PHP extensions
RUN apt-get install -y libicu-dev libpng-dev libzip-dev
RUN docker-php-ext-install intl gd zip mysqli && docker-php-ext-enable mysqli

# Modify php.ini to increase upload file size to 100MB
RUN echo "upload_max_filesize = 100M" > /usr/local/etc/php/conf.d/uploads.ini
RUN echo "post_max_size = 100M" >> /usr/local/etc/php/conf.d/uploads.ini

# Install composer
# RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install git
# RUN apt-get install -y git

# Enable mod_rewrite for Apache
RUN a2enmod rewrite

# Copy the Apache configuration file
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

# Restart Apache
RUN service apache2 restart