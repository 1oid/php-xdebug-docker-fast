FROM php:7.3-fpm

RUN apt-get update \
    && apt install -y libwebp-dev libjpeg-dev libpng-dev libfreetype6-dev \
    && docker-php-source extract \
    && cd /usr/src/php/ext/gd \
    && docker-php-ext-configure gd --with-webp-dir=/usr/include/webp --with-jpeg-dir=/usr/include --with-png-dir=/usr/include --with-freetype-dir=/usr/include/freetype2 \
    && docker-php-ext-install gd
RUN apt install -y libwebp-dev libjpeg-dev libpng-dev libfreetype6-dev
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo pdo_mysql \
    && docker-php-ext-install gd
RUN echo 'xdebug.remote_port=9000' >> /usr/local/etc/php/php.ini
RUN echo 'xdebug.remote_enable=1' >> /usr/local/etc/php/php.ini
RUN echo 'xdebug.remote_connect_back=1' >> /usr/local/etc/php/php.ini
RUN echo 'extension=pdo_mysql.so' >> /usr/local/etc/php/php.ini
RUN echo 'cgi.fix_pathinfo=1' >> /usr/local/etc/php/php.ini