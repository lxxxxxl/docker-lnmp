FROM php:7.3-fpm

RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak \ 
    && echo "deb http://mirrors.aliyun.com/debian/ stretch main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb-src http://mirrors.aliyun.com/debian/ stretch main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian-security stretch/updates main" >> /etc/apt/sources.list \
    && echo "deb-src http://mirrors.aliyun.com/debian-security stretch/updates main" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian/ stretch-updates main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb-src http://mirrors.aliyun.com/debian/ stretch-updates main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.aliyun.com/debian/ stretch-backports main non-free contrib" >> /etc/apt/sources.list \
    && echo "deb-src http://mirrors.aliyun.com/debian/ stretch-backports main non-free contrib" >> /etc/apt/sources.list \
    && apt-get clean \
    && apt-get update \
    && apt-get install -yf make gcc g++ curl wget git

# 
RUN docker-php-ext-install pdo_mysql \
    && pecl install redis && docker-php-ext-enable redis \
    && pecl install xdebug && docker-php-ext-enable xdebug \
    && pecl install swoole && docker-php-ext-enable swoole
    
# Composer
ADD composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer
