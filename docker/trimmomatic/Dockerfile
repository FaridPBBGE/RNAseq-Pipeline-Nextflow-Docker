# Use a slim Ubuntu base
FROM ubuntu:22.04

# Metadata
LABEL maintainer="faridpbbge"
LABEL description="Trimmomatic v0.39 for adapter trimming"
LABEL version="0.40"

# 3. ENVIRONMENT VARIABLES
# Prevents Java/Ubuntu from asking for timezone/keyboard input
ENV DEBIAN_FRONTEND=noninteractive
# Being explicit about the path for our wrapper script
ENV PATH="/usr/local/bin:$PATH"


# 1. Install Java (Required for Trimmomatic) and tools
RUN apt-get update && apt-get install -y \
    openjdk-11-jre-headless \
    wget \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# 2. Download and Setup Trimmomatic
WORKDIR /opt
RUN wget https://github.com/usadellab/Trimmomatic/releases/download/v0.40/Trimmomatic-0.40.zip && \
    unzip Trimmomatic-0.40.zip && \
    rm Trimmomatic-0.40.zip

# 3. Create a "Wrapper Script" 
# This lets me type 'trimmomatic' instead of 'java -jar /opt/Trimmomatic-0.39/trimmomatic.jar'
RUN echo '#!/bin/bash\njava -jar /opt/trimmomatic-0.40.jar "$@"' > /usr/local/bin/trimmomatic && \
    chmod +x /usr/local/bin/trimmomatic

# 4. Set working directory for the user
WORKDIR /data

# Default command
ENTRYPOINT ["trimmomatic"]
