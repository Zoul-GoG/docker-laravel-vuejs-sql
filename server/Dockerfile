FROM php:8.0.5
RUN apt-get update -y && apt-get install -y openssl zip unzip git libonig-dev
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN docker-php-ext-install pdo pdo_mysql mbstring
WORKDIR /app
COPY ./api_laravel /app
# RUN composer install # Not needed because docker at first "executes" Dockerfile (until CMD command) after that mount volumes. https://stackoverflow.com/a/48810282

CMD php artisan serve --host=0.0.0.0 --port=8001
EXPOSE 8001

# https://stackoverflow.com/a/59664416   Laravel - What steps should one take to make a Laravel app ready for production mode