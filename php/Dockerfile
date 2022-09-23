FROM php:7.4.30-fpm 
RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip \
    && docker-php-ext-install intl opcache mysqli pdo pdo_mysql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN curl -sS https://get.symfony.com/cli/installer | bash
COPY . /
WORKDIR /Hotel-Management
RUN composer install
RUN php artisan key:generate
CMD  php artisan serve --host=0.0.0.0 --port=7000
EXPOSE 7000



