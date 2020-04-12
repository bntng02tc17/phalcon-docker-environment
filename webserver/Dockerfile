
#PHALCON REQUIREMENT
FROM php:7.3-apache
RUN apt-get -y update && apt-get -y upgrade
ADD https://raw.githubusercontent.com/mlocati/docker-php-extension-installer/master/install-php-extensions /usr/local/bin/
RUN chmod uga+x /usr/local/bin/install-php-extensions && sync && \
    install-php-extensions gd xdebug sqlsrv pdo_sqlsrv imagick memcached
RUN pecl install psr && docker-php-ext-enable psr
RUN apt-get update && apt-get -y install gnupg2
RUN apt-get -y install libpcre3-dev
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
RUN curl https://packages.microsoft.com/config/debian/10/prod.list > /etc/apt/sources.list.d/mssql-release.list
RUN apt-get -y update && ACCEPT_EULA=Y apt-get install msodbcsql17
RUN ACCEPT_EULA=Y apt-get install mssql-tools
RUN apt-get -y install unixodbc-dev
#RUN apt-get -y install libgssapi-krb5-2
RUN pecl install phalcon && docker-php-ext-enable phalcon
COPY ./example.local.conf /etc/apache2/sites-available/