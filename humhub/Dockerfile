# syntax=docker/dockerfile:1

FROM humhub/humhub:stable

USER root

COPY certs /tmp/certs

RUN if ls /tmp/certs/*.crt >/dev/null 2>&1; then \
        cp /tmp/certs/*.crt /usr/local/share/ca-certificates/; \
        update-ca-certificates; \
    fi \
    && rm -rf /tmp/certs
