# NoBrainer

## ✍️ Introduction

This project is a self-hosted "second brain" knowledge base built with Obsidian,
version-controlled and backed up through a self-hosted Gitea instance, and
connected to Claude via MCP so months of notes can be queried directly instead
of manually searched through.

It solves a real problem: notes and documentation scattered across classes,
projects, and internships, with no reliable way to find or back them up later.

## 🛠️ Tools Used

---

- Obsidian
- Obsidian Git (community plugin)
- MCP Connector (Obsidian community plugin)
- Docker Desktop
- Gitea
- Git
- Claude Desktop

---

## Architecture

The vault lives locally as a normal Obsidian vault. Docker Desktop runs a
self-hosted Gitea instance in a container, which acts as the private git
remote for the vault. The Obsidian Git plugin auto-commits and auto-pushes
changes to Gitea on an interval, authenticated with a Gitea personal access
token. The MCP Connector plugin exposes the vault over a local MCP endpoint,
which Claude Desktop connects to, allowing the vault's notes to be searched
and referenced in conversation without manually digging through folders.

## Setup Walkthrough

**Self-hosted Git server**

I ran Gitea in a Docker container using a `docker-compose.yml`, mapping the
web UI to port 3000 and SSH to port 2222, with repository data persisted to
a local volume. SQLite3 was used as the database for simplicity.

**Connecting the vault**

I initialized the vault folder as a git repository and pushed it to a new
private repository on the self-hosted Gitea instance.

**Automating sync**

I configured the Obsidian Git plugin to automatically commit and push changes
on an interval. Authentication uses a Gitea personal access token (scoped to
repository read/write) so the automated pushes don't require manual sign-in.

**Connecting Claude via MCP**

I used the Obsidian MCP Connector plugin, which runs a local MCP server
directly from the vault and generates a ready-to-use Claude Desktop config
(including a bearer token for authentication). Claude Desktop connects to
this local endpoint, giving it the ability to search and reference notes
across the whole vault on request.

## 📁 Files

- `docker-compose.yml` - Gitea service definition (image, ports, volumes)
- `claude_desktop_config.json` (not included/committed - contains a secret
  token) - MCP client configuration connecting Claude Desktop to the vault's
  local MCP endpoint

## Conclusion

This project turned a growing, scattered pile of personal notes into a
searchable, version-controlled, self-hosted knowledge base that I use daily.
Along the way I got hands-on practice with Docker, self-hosted git hosting,
git automation, and MCP.

## Next Steps

- Move Gitea from a container on my daily-driver PC into an isolated VM
- Add ZFS-backed storage and automated snapshots for disaster recovery
- Eventually migrate to dedicated hardware with Proxmox
