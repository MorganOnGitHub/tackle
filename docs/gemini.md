# Tackle for Gemini CLI

Tackle installs as a Gemini CLI extension. The extension provides:

- `skills/`: the Tackle skills. Gemini sees each skill's name and description at startup and loads the full skill with `activate_skill` when a description matches.
- `GEMINI.md`: a short context note (about 100 words) covering precedence and Gemini's tool names, loaded each session.

## Availability

Since June 18, 2026, Gemini CLI no longer serves free-tier or Google AI Pro/Ultra users; Google moved those users to Antigravity CLI. It still works with a Gemini Code Assist Standard or Enterprise license, or with paid Gemini API keys. On Antigravity CLI, see [Antigravity CLI](#antigravity-cli) below.

## Install

From a repository:

```bash
gemini extensions install <tackle-repo-url>
```

From a local checkout, for development (edits take effect without reinstalling):

```bash
gemini extensions link /path/to/tackle
```

Restart Gemini CLI after installing.

## Subagents

Gemini CLI has subagents on by default. Each one is exposed to the main agent as a tool with the subagent's name:

- `generalist` has the main agent's tools and suits implementation tasks, so `delegating-to-subagents` dispatches work to it
- `codebase_investigator` is for read-only research, which fits `investigating-in-parallel`

If subagents are turned off (`"experimental": { "enableAgents": false }` in `settings.json`), the skills fall back to working in a single session. See `skills/using-tackle/references/platforms.md`.

## Verify

Inside a Gemini CLI session:

```
/extensions list
/skills list
```

Tackle should appear in the extensions list, and its 14 skills in the skills list. Then ask something that should trigger a skill, such as "this test fails intermittently, help me find out why". Gemini should activate `debugging-systematically`. For a trivial request like "fix the typo on line 3", it should just fix it.

## Update

```bash
gemini extensions update tackle
```

Linked installs update as you edit the checkout.

## Uninstall

```bash
gemini extensions uninstall tackle
```

## Antigravity CLI

Antigravity CLI keeps Agent Skills, subagents and extensions; extensions become Antigravity plugins. Migration reports describe importing an installed Gemini extension with `agy plugin import`. Tackle hasn't been tested on Antigravity yet, so after migrating, check that its skills are listed.

## Troubleshooting

- **Skills missing from `/skills list`:** run `/skills reload`, then check the extension is enabled in `/extensions list`.
- **Running alongside superpowers:** uninstall or disable the superpowers extension where you use Tackle. Its `GEMINI.md` loads its own skill rules into every session.
