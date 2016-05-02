FROM php:7.0-fpm
RUN curl -L https://github.com/xdebug/xdebug/archive/XDEBUG_2_4_0.tar.gz -o XDEBUG_2_4_0.tar.gz \
   && tar -zxvf XDEBUG_2_4_0.tar.gz \
   && rm XDEBUG_2_4_0.tar.gz \
   && cd xdebug-XDEBUG_2_4_0 \
   && phpize \
   && ./configure --enable-xdebug \
   && make \
   && make install \
   && cd ../ && rm -r xdebug-XDEBUG_2_4_0

RUN docker-php-ext-install opcache pdo
RUN apt-get update && \
    apt-get install -y libpq-dev && rm -r /var/lib/apt/lists/*
RUN docker-php-ext-install pdo_pgsql

RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer
RUN apt-get update && apt-get install -y git zip unzip \
    && rm -rf /var/lib/apt/lists/*
WORKDIR /opt/yat

RUN usermod -u 1000 www-data
