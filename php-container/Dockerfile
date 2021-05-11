ARG BIGFORUM_PHP_VERSION

FROM php:${BIGFORUM_PHP_VERSION}-apache

ARG BIGFORUM_VERSION
ARG BIGFORUM_USE_CUSTOM_DATA

RUN docker-php-ext-install mysql pdo pdo_mysql

RUN if [ "${BIGFORUM_USE_CUSTOM_DATA}" = "enabled" ]; then \
      cd /var/www; \
      rm -r /var/www/html; \
      ln -s "/var/www/html-custom" "html"; \
    else \
      ls -l /var/www/; \
      curl -sL "https://github.com/bigforum/bigforum/archive/refs/tags/v${BIGFORUM_VERSION}.tar.gz" -o "bigforum.tar.gz"; \
      tar xvzf "bigforum.tar.gz" --strip-components=1 -C "/var/www/html"; \
      mv "/var/www/html/.htaccess" "/var/www/html/.htaccess.disabled" || true; \
    fi \
    && chown -R www-data:www-data /var/www/html
