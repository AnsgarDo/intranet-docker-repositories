# syntax=docker/dockerfile:1

FROM humhub/humhub:stable

USER root

COPY certs/*.crt /usr/local/share/ca-certificates/

RUN update-ca-certificates
