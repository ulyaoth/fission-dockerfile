# Define the base builder image and Python base image versions
ARG BUILDER_IMAGE=fission/builder
ARG PY_BASE_IMG=3.12.4-alpine

# Stage 1: Use the Fission builder base image
FROM ${BUILDER_IMAGE} AS fission-builder

# Stage 2: Use the specified Python base image
FROM python:${PY_BASE_IMG}

# Copy the builder files from the first stage
COPY --from=fission-builder /builder /builder

# Install necessary build tools and libraries
RUN apk add --update --no-cache linux-headers gcc python3-dev libffi-dev build-base bash

# Upgrade pip to the latest version
RUN pip install --upgrade pip

# Add the default build command to the PATH
ADD defaultBuildCmd /usr/local/bin/build

# Expose the builder port
EXPOSE 8001

