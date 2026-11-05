# Claude Code on the Synology

Runs the Claude Code CLI in a container (DS423+, x86_64, DSM 7.2+ Container Manager).

## Setup (over SSH)
```
mkdir -p /volume1/docker/appdata/claude-code/home
sudo chown 1026:100 /volume1/docker/appdata/claude-code/home
git clone https://github.com/samcollender/synology-docker-configs /volume1/docker/synology-docker-configs
cd /volume1/docker/synology-docker-configs/claude-code
sudo docker compose up -d --build
sudo docker exec -it claude-code claude
```
First run asks you to log in (Claude Pro/Max account or API key). Login persists in the home volume.

## Notes
- Only `/workspace` (the repo clone) is visible to Claude. Mount more folders deliberately.
- Credentials in `.env` files inside the mounted folder are readable by Claude.
- Update: `sudo docker compose build --no-cache && sudo docker compose up -d`.
- Adjust PUID/PGID if your DSM user isn't 1026:100 (`id` over SSH).
