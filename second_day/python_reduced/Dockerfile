# First stage: build environment using Ubuntu
FROM ubuntu:latest as builder

# Set non-interactive mode for apt-get
ENV DEBIAN_FRONTEND=noninteractive

# Install Python and dependencies
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv

# Set the working directory
WORKDIR /app

# Copy the requirements file and install dependencies in a virtual environment
COPY requirements.txt requirements.txt
RUN python3 -m venv venv && \
    ./venv/bin/pip install -r requirements.txt

# Copy the application code
COPY hello.py app.py

# Second stage: runtime environment using Alpine
FROM alpine:latestd

# Install Python 3 in Alpine
RUN apk add --no-cache python3 py3-pip

# Set the working directory
WORKDIR /app

# Copy the virtual environment and application code from the builder stage
COPY --from=builder /app/venv /app/venv
COPY --from=builder /app/app.py /app/app.py

# Ensure the virtual environment uses the correct interpreter
ENV PATH="/app/venv/bin:$PATH"

# Expose the port for the application
EXPOSE 8000

# Define the command to run the application
CMD ["python", "app.py"]