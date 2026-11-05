FROM node:22-bookworm-slim

RUN apt-get update \
 && apt-get install -y --no-install-recommends git openssh-client ca-certificates curl less \
 && rm -rf /var/lib/apt/lists/*

RUN npm install -g @anthropic-ai/claude-code

# Match the Synology user/group used by the other stacks so bind-mounted files stay writable
ARG PUID=1026
ARG PGID=100
RUN (getent group ${PGID} || groupadd -g ${PGID} claude) \
 && useradd -m -u ${PUID} -g ${PGID} -s /bin/bash claude

USER claude
WORKDIR /workspace
CMD ["sleep", "infinity"]
