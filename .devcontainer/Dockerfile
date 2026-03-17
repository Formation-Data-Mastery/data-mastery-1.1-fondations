FROM ubuntu:24.04

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    ca-certificates \
    sudo \
    git \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash apprenant \
    && echo "apprenant ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER apprenant
WORKDIR /workspaces/data-mastery-1.1-fondations

CMD ["sleep", "infinity"]
