FROM python:3.9-slim

# Metadata
LABEL maintainer="faridpbbge"
LABEL description="Aggregate bioinformatics results across many samples into a single report"
LABEL version="1.21"

# ENVIRONMENT VARIABLES
ENV DEBIAN_FRONTEND=noninteractive

# Install dependicies
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Install MultiQC via pip
RUN pip3 install --no-cache-dir multiqc==1.21

# Set working directory
WORKDIR /data

# Default command
ENTRYPOINT ["multiqc"]
CMD ["--help"]
