# syntax=docker/dockerfile:1.29@sha256:572cebbc2b15e6f84c077742952674889cb63cd5e9b80abdffcbe587b6f19183
FROM alpine:3.24@sha256:f59abe656b692d901e184be3445e084786602108599d2a51d229c0f5a48c71bf

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
