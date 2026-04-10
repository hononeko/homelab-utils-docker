# syntax=docker/dockerfile:1.4
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
