# Sandbox

Infrastructure as Code for my Windows/Linux lab.

## Goal

Rebuild **LINUX01** from a clean Ubuntu Server installation using Ansible.

The project aims to produce a fully configured enterprise-style Linux server, including:

- Active Directory domain membership (Winbind)
- Kerberos authentication
- Samba file server
- Docker Engine
- Self-hosted services

Each component is implemented as an independent, idempotent Ansible role to allow repeatable deployments from a fresh installation.