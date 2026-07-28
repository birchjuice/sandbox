# Sandbox

Infrastructure as Code for my Windows/Linux lab.

## Goal

Provision **LINUX01** from a clean Ubuntu Server installation using Ansible, resulting in a fully configured domain member with all infrastructure services deployed automatically.

## Features

- Active Directory domain integration
- Samba file server
- Docker
- MariaDB
- Gitea
- Nginx reverse proxy
- BIND DNS
- Prometheus monitoring
- Grafana dashboards


# Repository Conventions

## General

- One role owns one service.
- Prefer short Ansible module names (no FQCNs).
- Prefer single quotes over double quotes.
- Keep tasks simple and readable; avoid unnecessary abstraction.

## Variables

- Store all configurable values in `group_vars`.
- Passwords and secrets are stored in `group_vars` and encrypted with Ansible Vault.
- Service ports are always variables.
- If a value is expected to change, make it a variable.

## Networking

- Avoid hardcoded IP addresses whenever a hostname or `localhost` can be used.
- Infrastructure IP addresses belong only in `group_vars`.
- DNS records and similar IP-specific configuration belong in the `bind` role.

## Templates

- Prefer one well-structured template over many tiny templates when it improves readability.
- Keep templates focused on configuration rather than business logic.

## Monitoring

- Monitoring configuration lives with the monitored service.
- Prometheus scrape jobs live in the Prometheus role.
- Grafana dashboards are provisioned and stored in Git.

## Idempotency

- Tasks should be idempotent whenever practical.
- Use handlers instead of unnecessary service restarts.