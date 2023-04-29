#The base image for the container
FROM python:3.10.11-slim-buster

RUN apt-get update && \
    apt-get install -y --no-install-recommends git curl && \
    apt-get purge -y --auto-remove && \
    rm -rf /var/lib/apt/lists/*

RUN python -m ensurepip

# Keeps Python from generating .pyc files in the container
ENV PYTHONDONTWRITEBYTECODE=1

# Turns off buffering for easier container logging
ENV PYTHONUNBUFFERED=1

# Copy python requirements to the docker container and install
COPY requirements.txt .
RUN python -m pip install -r requirements.txt

#create a non root user to access the container
RUN groupadd --gid 1000 vscode \
    && useradd --uid 1000 --gid vscode --shell /bin/bash --create-home vscode
