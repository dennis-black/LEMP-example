FROM ubuntu:latest

# Update and install necessary packages
RUN apt update && \
    apt upgrade -y && \
    apt install -y \
    build-essential \
    curl \
    zip \
    vim \
    git \
    apache2 \
    php \
    php-mbstring \
    php-mysql \
    php-curl

# start apache mod_rewrite (must check 'AllowOverride All')
RUN a2enmod rewrite

# Install php-composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

EXPOSE 80

# Set the working directory
WORKDIR /var/www/html

# Start services using Supervisor
CMD ["apache2ctl", "-D", "FOREGROUND"]
