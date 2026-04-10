# syntax=docker/dockerfile:1.23@sha256:2780b5c3bab67f1f76c781860de469442999ed1a0d7992a5efdf2cffc0e3d769
FROM alpine:3.23@sha256:25109184c71bdad752c8312a8623239686a9a2071e8825f20acb8f2198c3f659

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
