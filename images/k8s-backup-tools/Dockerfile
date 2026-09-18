# syntax=docker/dockerfile:1.27@sha256:bde3983e9c939224420ddaf6b784cc30e09b035a4dea01f581230c50809f372e
FROM alpine:3.24@sha256:294b683cb724975bec92580e1e685676bd4b50bda910ddb8c51d4cabeaec77e6

# Install the minimal tools required for typical Kubernetes active volume syncs and SQLite manipulations
RUN apk add --no-cache \
    rsync \
    inotify-tools \
    findutils \
    sqlite \
    bash \
    coreutils \
    catatonit

# Set a lightweight, reaping init process
ENTRYPOINT ["/usr/bin/catatonit", "--"]
CMD ["/bin/sh"]
