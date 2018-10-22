FROM srcoder/development-php:php7-fpm
LABEL maintainer="Jeroen Boersma <jeroen@srcode.nl>"

RUN apt-get update --fix-missing && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        msmtp \
        imagemagick \
        libssl-dev \
        libxml2-dev \
        libicu-dev \
        libxslt-dev \
        wget libcurl4-openssl-dev \
        unzip \
        ssh-client git vim \
    && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install mcrypt bcmath mysql mysqli pdo_mysql mbstring ftp soap zip opcache intl xsl \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

# Install xdebug and redis
RUN pecl install xdebug-2.5.5 redis-4.1.1 \
    && docker-php-ext-enable xdebug redis \
    && rm -rf /tmp/pear

# Install AMPQ and RabbitMQ Libs
RUN apt-get update \
    && apt-get install -y \
        librabbitmq-dev \
        libssh-dev \
    && docker-php-ext-install \
        bcmath \
        sockets \
    && pecl install amqp \
    && docker-php-ext-enable amqp


ARG GID=1000
ARG UID=1000

RUN groupmod -g $GID app && \
    usermod -g $GID -u $UID app
