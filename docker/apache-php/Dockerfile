FROM php:7.4-apache
ENV COMPOSER_ALLOW_SUPERUSER=1





RUN apt update &&\
	apt upgrade -y &&\
	DEBIAN_FRONTEND=noninteractive apt install -y \
	curl \
	gnupg2 \
	gcc \
	g++ \
	make \
	git \
	unzip \
	libzip-dev \
	libpng-dev \
	zlib1g-dev \
	libicu-dev \
	screen \
	nano \
	telnet \
	net-tools


RUN docker-php-ext-install -j$(nproc) zip opcache bcmath exif gd

#INTL
RUN docker-php-ext-install -j$(nproc) intl

ADD conf/php.ini /usr/local/etc/php/conf.d/app.ini

RUN apt-get update -qy && \
	apt-get upgrade -y && \
    apt-get install -y \
    git \
    libicu-dev \
    unzip \
    zip

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer




#add nodejs
RUN curl -sL https://deb.nodesource.com/setup_13.x | bash \
    && apt-get update && apt-get install nodejs -yq


RUN curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
     echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list  && \
     apt-get update && apt-get install yarn



RUN a2enmod proxy_fcgi setenvif headers rewrite





RUN ln -sf /usr/share/zoneinfo/Europe/Paris /etc/localtime




RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 80

