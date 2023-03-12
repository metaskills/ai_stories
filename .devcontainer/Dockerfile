# Shared image, envs, packages for both devcontainer & prod.
FROM ruby:3.2-bullseye
RUN apt update

# Temporary multi-platform SAM CLI install method.
# https://github.com/aws/aws-sam-cli/issues/3908
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3 1
RUN apt-get install -y pip && pip install aws-sam-cli

# Postgres client.
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive && \
    apt-get -y dist-upgrade && \
    apt-get install -y \
      libpq-dev \
      postgresql-client

# Local devcontainer Codespaces compatibility.
RUN mkdir -p /workspaces/ai_stories
ENV BUNDLE_IGNORE_CONFIG=1
ENV BUNDLE_PATH=./vendor/bundle
ENV BUNDLE_CACHE_PATH=./vendor/cache
