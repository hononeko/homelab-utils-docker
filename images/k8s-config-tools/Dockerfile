# syntax=docker/dockerfile:1.27@sha256:bde3983e9c939224420ddaf6b784cc30e09b035a4dea01f581230c50809f372e
FROM alpine:3.24@sha256:294b683cb724975bec92580e1e685676bd4b50bda910ddb8c51d4cabeaec77e6

# Install common config management utilities
RUN apk add --no-cache \
    gomplate \
    yq \
    jq \
    curl \
    bash \
    catatonit

# Set a lightweight, reaping init process
ENTRYPOINT ["/usr/bin/catatonit", "--"]
CMD ["/bin/sh"]
