ARG PHP_TAG

FROM docker.io/library/php:$PHP_TAG

ARG PHP_REDIS_VERSION

RUN cd ~ && echo "php_redis: $PHP_REDIS_VERSION " \
     && wget https://github.com/phpredis/phpredis/archive/$PHP_REDIS_VERSION.tar.gz && tar -zxvf $PHP_REDIS_VERSION.tar.gz \
     && mkdir -p /usr/src/php/ext \
     && mv phpredis-$PHP_REDIS_VERSION /usr/src/php/ext/redis
RUN  docker-php-ext-install redis

#### 扩展
RUN apk add libstdc++ libpng-dev

#RUN docker-php-ext-install pdo_mysql mysqli pcntl gd
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install pcntl
RUN docker-php-ext-install gd


RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

