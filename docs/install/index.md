# Installation

Tracedown is a set of JVM services, a Python probe agent, PostgreSQL, and Redis.
Everything runs in Docker, and the supplied Compose stack brings up a working
system in one command.

Read these in order:

1. **[Requirements](requirements.md)** — what you need before you start.
2. **[Quickstart (Docker)](quickstart.md)** — a running system in a few minutes.
3. **[Architecture](architecture.md)** — what the services are and how they talk.
4. **[Configuration](configuration.md)** — the full environment-variable reference.
5. **[Database & Migrations](database.md)** — how schema changes are applied.
6. **[Probe Agents](agents.md)** — deploying agents and enrolling them over mTLS.

!!! warning "The Compose stack ships with development secrets"
    The bundled `.env.example` contains a placeholder encryption key, a placeholder JWT
    secret, and a known demo password. They are fine for a local trial and
    unacceptable for anything reachable by other people. Before you expose
    Tracedown to a network, work through **[Secrets & Encryption](../admin/secrets.md)**.

## Which pieces are optional

| Piece | Needed? |
|---|---|
| PostgreSQL | Required. System of record. |
| Redis A | Required. Queues, outbox, sessions — persistent (AOF). |
| Redis B | Required in practice. Cache and rate limiting; safe to lose. |
| Redis C | Optional. Resource-hierarchy cache; disabled when `REDIS_C_URL` is empty. |
| Probe agent | Required — nothing probes without at least one agent. |
| S3-compatible storage | Optional. Only if you want saved response bodies off local disk. |
| SMTP / Resend / Mailgun | Optional, but without it no email leaves the system. |

## After installation

Once the stack is up and an agent is enrolled, the **[User Manual](../guide/index.md)**
covers creating your first service and probe. The **[Administration](../admin/index.md)**
section covers the things you only think about once it is real: backups,
certificate rotation, retention, and scaling.
