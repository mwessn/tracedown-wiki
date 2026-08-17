# tracedown-wiki

The Tracedown documentation site — built with mkdocs-material, live at
[tracedown.dev](https://tracedown.dev).

Tracedown is a self-hosted API monitoring platform; the code lives in
[tracedown-core-backend](https://github.com/tracedown/tracedown-core-backend),
[tracedown-core-frontend](https://github.com/tracedown/tracedown-core-frontend)
and [tracedown-probe-agent](https://github.com/tracedown/tracedown-probe-agent).
Probes are written in [Lace](https://lacelang.dev).

## Local preview

```bash
pip install mkdocs-material ./pygments-lace
mkdocs serve
```

`mkdocs build` renders the static site into `site/`. The `Dockerfile` builds
that site and serves it with nginx, listening on the `$PORT` environment
variable.

The `pygments-lace/` package provides the ```` ```lace ```` fence highlighter
and is vendored from the [lacelang](https://github.com/tracedown/lacelang)
repo's wiki. Keep it in sync when the Lace grammar changes.

## License

Open source under the Apache License 2.0. See `LICENSE`.
