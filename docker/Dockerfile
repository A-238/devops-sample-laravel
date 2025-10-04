FROM php:8.2-cli

RUN apt-get update && apt-get install -y unzip git \
 && docker-php-ext-install pdo pdo_mysql

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Laravel 用ディレクトリを指定
WORKDIR /var/www/laravel

RUN composer create-project laravel/laravel . --prefer-dist --no-interaction

RUN php artisan key:generate

EXPOSE 8000

CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8000"]
