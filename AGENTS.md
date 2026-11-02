# AGENTS.md: Relacion Codex exchange repo

Shared exchange point for the one-week Codex pilot (Grok Bot fleet coordinates, and Codex cloud builds).

Rules for any agent working here:
- Work on a branch and open a PR. Never push to main.
- One task per PR. Each task's brief is in tasks/<id>.md. Code lives in src/<id>/, with tests beside it.
- No secrets, tokens, client names or $ figures in code, tests, fixtures or PR text.
- No network calls to live services. Never call Airbyte or any reporting-refresh endpoint. Use fixtures only.
- Python 3.11, standard library plus pytest. Run `pytest -q` before opening the PR, and paste the result in the PR body.
- Keep PRs small. Explain what changed and how it was verified, in 10 lines or fewer.
