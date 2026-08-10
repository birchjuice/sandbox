# Sandbox

Infrastructure as Code for my Windows/Linux lab.

## Goal

Provision **LINUX01** from a clean Ubuntu Server installation using Ansible, resulting in a fully configured Active Directory domain member with file sharing, monitoring, internal DNS and TLS, and SSO services deployed automatically.

## Features

* AD integration
* Samba file server
* Docker
* BIND DNS
* Keycloak SSO
* Nginx HTTPS reverse proxy
* Gitea
* Grafana
* Prometheus

## Repository Conventions

### General

* Each service has a clear owning role.
* Prefer short Ansible module names.
* Prefer single quotes over double quotes.
* Keep tasks simple and readable; avoid unnecessary abstraction.

### Variables

* Store configurable values in `group_vars`.
* Store passwords and secrets in `group_vars` encrypted with Ansible Vault.
* Configurable service ports are variables.

### Networking

* Avoid hardcoded IP addresses when a hostname or `localhost` can be used.
* Infrastructure IP addresses are defined in `group_vars`.
* DNS configuration belongs in the `bind` role.

### Monitoring

* Monitoring configuration lives with the monitored service.
* Prometheus scrape jobs live in the Prometheus role.
* Grafana dashboards are provisioned and stored in Git.

### Idempotency

* Tasks should be idempotent whenever practical.
* Use handlers instead of unnecessary service restarts.
