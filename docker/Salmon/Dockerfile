# Use a slim Ubuntu base
FROM ubuntu:22.04

# Metadata
LABEL maintainer="faridpbbge"
LABEL description="Salmon 1.10.0 for counting transcripts"
LABEL version="1.10.0"

# ENVIRONMENT VARIABLES
# Prevents Java/Ubuntu from asking for timezone/keyboard input
ENV DEBIAN_FRONTEND=noninteractive
# Setup ENV path
ENV PATH="/opt/salmon-latest_linux_x86_64/bin:$PATH"

# Install dependecies tools
RUN apt-get update && apt-get install -y \
    wget \
    libcurl4-openssl-dev \
    libbz2-dev \
    liblzma-dev \
    && rm -rf /var/lib/apt/lists/*

# Download and Setup
WORKDIR /opt
RUN wget https://github.com/COMBINE-lab/salmon/releases/download/v1.10.0/salmon-1.10.0_linux_x86_64.tar.gz && \
    tar xzf salmon-1.10.0_linux_x86_64.tar.gz && \
    rm salmon-1.10.0_linux_x86_64.tar.gz

# Set working directory
WORKDIR /data

# Default command
ENTRYPOINT ["salmon"]
CMD ["--help"]
