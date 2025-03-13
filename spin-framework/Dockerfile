# Use official PHP image with Apache
FROM php:8.2-apache

# Set working directory
WORKDIR /app

RUN apt-get update && apt-get install -y unzip git curl nano wget sudo

RUN echo "apache:x:1000:1000::/home/user:/bin/bash" >> /etc/passwd \
  && echo "apache:x:1000:" >> /etc/group \
  && mkdir -p /home/apache \
  && chown 1000:1000 /home/apache \
  && usermod -aG sudo apache \
  && echo "apache ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# Install required packages
#RUN apt-get update && apt-get install -y \
#    unzip \
#    git \
#    curl \
#    libpng-dev \
#    libjpeg-dev \
#    libfreetype6-dev \
#    libzip-dev \
#    && docker-php-ext-configure gd --with-freetype --with-jpeg \
#    && docker-php-ext-install gd zip pdo pdo_mysql

# Enable Apache mod_rewrite
RUN a2enmod rewrite

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#RUN composer require celarius/spin-framework

# Expose Apache port
EXPOSE 80

# Set entrypoint command
#CMD ["apache2-foreground"]