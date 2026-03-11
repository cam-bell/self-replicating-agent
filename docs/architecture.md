# Architecture Notes

This repository centers the distributed AutoGen runtime rather than the hosted demo surface.

## Why the distributed runtime is the primary story

The key technical value of the project is not just that multiple agents collaborate. The stronger systems signal is that the runtime can:

- start a gRPC host/worker topology
- generate new agents from Python source templates
- dynamically import and register those agents while the system is running
- orchestrate concurrent work across the generated agent set
- persist artifacts from each run

That is the implementation this repository is meant to preserve and explain.

## Why the demo is intentionally separate

The Hugging Face Space was adapted into a simpler single-process demo so it could be deployed reliably and shown to non-technical viewers. That makes it useful as a public surface, but it is not the full architectural story.

Keeping the demo separate avoids two problems:

- it prevents the GitHub repo from collapsing the distributed system into a hosted-only demo narrative
- it makes it easier to pursue a more faithful advanced deployment later, such as Render, without rewriting the core repo story again

## How to read the docs

- The main `README.md` is the portfolio-facing overview.
- `docs/diagrams/system-architecture.mmd` shows the distributed runtime boundary.
- `docs/diagrams/agent-workflow.mmd` shows the execution lifecycle for a run.
- `docs/diagrams/data-flow.mmd` shows how prompts, code, messages, and artifacts move through the system.
