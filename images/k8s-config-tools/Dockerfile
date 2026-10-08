# syntax=docker/dockerfile:1.28@sha256:bb22d9815c728170f72750f4e5b0d672e06176142e1d602c7e66c050100b7e5b
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
