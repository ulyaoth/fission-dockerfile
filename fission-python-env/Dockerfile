# Use the desired Python version, e.g., Python 3.12
ARG PY_BASE_IMG=3.12.5-alpine

FROM python:${PY_BASE_IMG}

WORKDIR /app

# Install necessary build tools and libraries
RUN apk add --update --no-cache gcc python3-dev build-base libev-dev libffi-dev bash

# Upgrade pip to the latest version
RUN pip install --upgrade pip

# Copy the requirements file and install dependencies
COPY requirements.txt /app
RUN pip install -r requirements.txt

# Copy the application code
COPY *.py /app

# Set environment variable using key=value format
ENV PYTHONUNBUFFERED=1

ENTRYPOINT ["python3"]
CMD ["server.py"]

