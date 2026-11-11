FROM xwiki:18.7.0-mariadb-tomcat

USER root

COPY certs /tmp/certs

RUN set -eux; \
    if ls /tmp/certs/*.crt >/dev/null 2>&1; then \
        for c in /tmp/certs/*.crt; do \
            n="$(basename "$c")"; \
            openssl x509 -in "$c" -out "/usr/local/share/ca-certificates/$n"; \
            keytool -importcert -noprompt -trustcacerts \
                -alias "${n%.crt}" \
                -cacerts \
                -storepass changeit \
                -file "/usr/local/share/ca-certificates/$n"; \
        done; \
        update-ca-certificates; \
    fi; \
    rm -rf /tmp/certs

USER root