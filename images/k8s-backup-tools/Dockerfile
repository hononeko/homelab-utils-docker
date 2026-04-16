# syntax=docker/dockerfile:1.23@sha256:2780b5c3bab67f1f76c781860de469442999ed1a0d7992a5efdf2cffc0e3d769
FROM alpine:3.23@sha256:5b10f432ef3da1b8d4c7eb6c487f2f5a8f096bc91145e68878dd4a5019afde11

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
