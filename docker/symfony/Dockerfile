FROM composer

#build symphony
RUN apk add  --no-cache --virtual wget \
    && docker-php-ext-install -j$(nproc) mysqli \
    && docker-php-ext-install -j$(nproc) pdo_mysql \
    && adduser -S symfony -G users -u 1000 \
    && wget https://get.symfony.com/cli/installer -O - | bash \
    && mv /root/.symfony/bin/symfony /usr/local/bin/symfony \
    && chmod 777 /home/symfony

USER symfony
WORKDIR /home/symfony/CENTRA-services/
VOLUME /home/symfony

CMD ["bash"]
