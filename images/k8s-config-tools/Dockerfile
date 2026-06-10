# syntax=docker/dockerfile:1.24@sha256:87999aa3d42bdc6bea60565083ee17e86d1f3339802f543c0d03998580f9cb89
FROM alpine:3.24@sha256:8ddefa941e689fc29abcdeb8dae3b3c6d139cc08ce9a52633931160701770685

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
