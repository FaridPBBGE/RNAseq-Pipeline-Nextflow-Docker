# Start with a clean Ubuntu system
FROM ubuntu:20.04

# Metadata
LABEL maintainer="faridpbbge"
LABEL description="fastqc for reads quality checking"
LABEL version="0.12.1"

#  ENVIRONMENT VARIABLES
# Prevents Java/Ubuntu from asking for timezone/keyboard input
ENV DEBIAN_FRONTEND=noninteractive
# Being explicit about the path for our wrapper script
ENV PATH="/opt/FastQC:$PATH"

# Install prerequisites (FastQC needs Java)
RUN apt-get update && apt-get install -y \
    openjdk-11-jre-headless \
    wget \
    unzip \
    perl \
    && rm -rf /var/lib/apt/lists/*

# Download and Install FastQC

WORKDIR /opt
RUN wget https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.12.1.zip && \
    unzip fastqc_v0.12.1.zip && \
    rm fastqc_v0.12.1.zip && \
    chmod +x /opt/FastQC/fastqc

# Set working directory
WORKDIR /data

#  Entrypoint for starting the tool
ENTRYPOINT ["fastqc"]
CMD ["--help"]
