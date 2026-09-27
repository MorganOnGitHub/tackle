# Tackle

This extension provides Tackle skills. Activate one with `activate_skill` when its description matches the task, and skip them for trivial tasks. The user's instructions and the system prompt always take precedence over any skill.

Tackle skills describe tools by role. On Gemini CLI:

- Run commands and tests: `run_shell_command`
- Track tasks: `write_todos`
- Ask a structured question: `ask_user`
- Dispatch a subagent: call the `generalist` subagent for implementation tasks, or `codebase_investigator` for read-only research. If subagents are disabled, use `executing-plans` instead of `delegating-to-subagents`.
