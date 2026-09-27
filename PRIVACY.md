# Privacy

**Tackle collects no data.**

Tackle is a set of Markdown instruction files. It has no MCP servers, no hooks, no install scripts, and no code that runs automatically when you install or use it. It makes no network requests.

Specifically, Tackle does not:

- collect, store or transmit personal data;
- read your code, files or conversations to anywhere outside your machine;
- include analytics, telemetry, crash reporting or usage tracking;
- set cookies or identifiers, or create accounts;
- share anything with third parties, because it sends nothing anywhere.

## What does handle your data

The coding agent you run Tackle in — Claude Code, Codex, Gemini CLI or another harness — processes your prompts and code, under its own privacy policy. Tackle changes how that agent approaches a task; it adds no data collection of its own and sends nothing to the author.

## About the eval harness

The repository includes a development tool at `evals/run.mjs` that contributors run by hand to measure whether a skill improves the agent's output. It is never executed by installing or using the plugin.

When a contributor runs it, it launches the Claude Code CLI already installed on that machine, against throwaway copies of test fixtures in a temporary directory. It reads environment variables for one purpose: to *remove* some of them — variables beginning with `CLAUDE` and plugin `bin` directories — so that the two arms of a benchmark are comparable. Nothing it reads is stored or sent anywhere, and it makes no network requests of its own.

## Children

Tackle is a developer tool. It is not directed at children and collects no information from anyone.

## Changes

Any change to this document will be made in this file, in the repository's public history.

## Contact

Questions or security concerns: <https://github.com/MorganOnGitHub/tackle/issues>
