# Use a slim Ubuntu base
FROM ubuntu:22.04

# Metadata
LABEL maintainer="faridpbbge"
LABEL description="STAR 2.7.10b for mapping"
LABEL version="2.7.10b"

# 3. ENVIRONMENT VARIABLES
# Prevents Java/Ubuntu from asking for timezone/keyboard input
ENV DEBIAN_FRONTEND=noninteractive
# Being explicit about the path for our wrapper script
ENV PATH="/opt/STAR-2.7.10b/source:$PATH"

#Install dependicies
RUN apt-get update && apt-get install -y \
    wget \
    zlib1g-dev \
    build-essential \
    && rm -rf /var/lib/apt/lists/*
# Install STAR
WORKDIR /opt
RUN wget https://github.com/alexdobin/STAR/archive/2.7.10b.tar.gz && \
    tar -xzf 2.7.10b.tar.gz && \
    cd STAR-2.7.10b/source && \
    make STAR

# 4. Set working directory for the user
WORKDIR /data

# Default command
ENTRYPOINT ["STAR"]
CMD ["--help"]
