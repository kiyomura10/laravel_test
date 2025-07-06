FROM php:8.3-fpm

#UTC +9
RUN apt-get update && \
    apt-get install -y tzdata && \
    ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    bash \
    curl \
    git \
    libjpeg62-turbo-dev \
    libpng-dev \
    libxml2-dev \
    libxslt-dev \
    libpq-dev \
    vim \
    redis-server \
    openssl && \
    rm -r /var/lib/apt/lists/*

    #php追加モジュールインストール
    RUN docker-php-ext-install pdo_pgsql soap

    RUN docker-php-ext-configure gd &&\
    NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
    docker-php-ext-install -j${NPROC} gd

    RUN rm -f /usr/local/etc/php-fpm.conf.default
    RUN rm -f /usr/local/etc/php-fpm.d/zz-docker.conf
    COPY php/php-fpm.conf /usr/local/etc/php-fpm.conf
    COPY php/php.ini /usr/local/etc/php/php.ini
    COPY php/www.conf /usr/local/etc/php-fpm.d/www.conf

    # composer install
RUN curl -sS https://getcomposer.org/installer | php -- --version=2.8.8 --install-dir=/usr/bin
RUN mv /usr/bin/composer.phar /usr/bin/composer

RUN mkdir -p /run/php

CMD ["/usr/local/sbin/php-fpm", "-F"]