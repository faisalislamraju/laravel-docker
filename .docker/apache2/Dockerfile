FROM php:7.2.7-apache

ARG uid
RUN useradd -G www-data,root -u $uid -d /home/testuser testuser
RUN mkdir -p /home/testuser/.composer && \
    chown -R testuser:testuser /home/testuser

RUN apt-get update --fix-missing -q
RUN apt-get install -y curl mcrypt gnupg build-essential software-properties-common wget vim zip unzip

RUN docker-php-ext-install pdo pdo_mysql

RUN curl -sSL https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ENV APACHE_DOCUMENT_ROOT=/var/www/html/public
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2/apache2.pid

RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf
RUN a2enmod rewrite

COPY . /var/www/html/

CMD ["/usr/sbin/apache2", "-DFOREGROUND"]
