FROM php:8.4-fpm-alpine

EXPOSE 9000

COPY docker/php/php.ini $PHP_INI_DIR/
COPY docker/php/zz-docker.conf /usr/local/etc/php-fpm.d/zz-docker.conf

RUN apk add --no-cache \
        tzdata \
        bash \
        icu-dev \
        icu-data-full \
        git \
        zip \
        libzip-dev \
        make \
    ;

RUN apk add --no-cache nodejs npm

RUN docker-php-ext-configure \
        intl \
        zip \
    ; \
    docker-php-ext-install \
        pdo \
        pdo_mysql \
        intl \
        zip \
    ; \
    docker-php-ext-enable \
        opcache \
    ;

RUN curl -1sLf "https://getcomposer.org/installer" | php -- \
    && mv composer.phar /usr/local/bin/composer

RUN curl -1sLf "https://dl.cloudsmith.io/public/symfony/stable/setup.alpine.sh" | version=3.8 bash \
    && apk add symfony-cli

RUN addgroup -g 1000 docker && adduser -G docker -g docker -s /bin/sh -D docker

RUN mkdir -p /socket \
    && chown -Rf docker:docker /socket

USER docker

RUN git config --global user.email "you@example.com" \
    &&  git config --global user.name "Your Name"

CMD [ "php-fpm" ]

WORKDIR /srv/app
