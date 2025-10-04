# Laravel用のDockerfile
FROM php:8.2-fpm

RUN apt-get update && apt-get install -y \
    unzip \
    git \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install pdo pdo_mysql gd

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/laravel

RUN composer create-project laravel/laravel . --prefer-dist --no-interaction

RUN php artisan key:generate

# 権限設定
RUN chown -R www-data:www-data /var/www/laravel
RUN chmod -R 755 /var/www/laravel/storage
RUN chmod -R 755 /var/www/laravel/bootstrap/cache

EXPOSE 9000

CMD ["php-fpm"]