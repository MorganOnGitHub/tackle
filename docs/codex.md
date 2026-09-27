# Tackle for Codex

Codex discovers skills natively: it scans `~/.agents/skills/` at startup, reads each `SKILL.md`'s frontmatter, and loads a skill when its description matches the task or you name it. Tackle needs no bootstrap or `AGENTS.md` changes; one link makes its skills visible.

## Install

1. **Get Tackle:**
   ```bash
   git clone <tackle-repo-url> ~/.codex/tackle
   ```
   Any location works; a local copy is fine too.

2. **Link the skills directory.**

   macOS / Linux:
   ```bash
   mkdir -p ~/.agents/skills
   ln -s ~/.codex/tackle/skills ~/.agents/skills/tackle
   ```

   Windows (PowerShell). A junction works without Developer Mode:
   ```powershell
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
   cmd /c mklink /J "$env:USERPROFILE\.agents\skills\tackle" "$env:USERPROFILE\.codex\tackle\skills"
   ```

3. **Restart Codex.** Skills are discovered at startup.

To share Tackle through a repository instead, link or copy `skills/` to `.agents/skills/` at the repo root; Codex also scans there.

## Subagents

Current Codex releases turn subagents on by default, so `delegating-to-subagents` and `investigating-in-parallel` work without setup. Use `/agent` to switch between running agent threads. To cap parallelism or choose the subagent model, set `max_concurrent_threads_per_session` and `default_subagent_model` under `[agents]` in `~/.codex/config.toml`.

If subagents are turned off (`[agents] enabled = false`), those skills fall back to working in a single session (see `skills/using-tackle/references/platforms.md`).

## Verify

Start Codex in a project and ask something that should trigger a skill, such as "this test fails intermittently, help me find out why". Codex should use `debugging-systematically`. For a trivial request like "fix the typo on line 3", it should just fix it.

## Update

```bash
cd ~/.codex/tackle && git pull
```

The link picks up changes immediately; restart Codex to reload.

## Uninstall

```bash
rm ~/.agents/skills/tackle
```

Windows: `Remove-Item "$env:USERPROFILE\.agents\skills\tackle"`. Then delete the clone if you no longer need it.

## Troubleshooting

- **Skills don't appear:** check the link resolves (`ls ~/.agents/skills/tackle/`) and restart Codex.
- **Running alongside superpowers:** remove `~/.agents/skills/superpowers` in setups where you use Tackle, so the two frameworks don't compete for the same situations.
