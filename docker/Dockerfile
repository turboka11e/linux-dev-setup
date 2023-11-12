# Use the official Ubuntu base image
FROM ubuntu:latest

# Install dependencies
RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y \
        software-properties-common \
        python3.11 \
        sudo \
        keychain
