FROM mysql:5.5

ARG BIGFORUM_USE_CUSTOM_DATA

RUN if [ "${BIGFORUM_USE_CUSTOM_DATA}" = "enabled" ]; then \
      rm -r "/docker-entrypoint-initdb.d"; \
      ln -s "/disabled-docker-entrypoint-initdb.d" "/docker-entrypoint-initdb.d"; \
    fi
