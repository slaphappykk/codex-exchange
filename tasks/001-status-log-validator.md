# Task 001: status.log line validator (pilot test build)

Build `src/statuslog/validate.py`, a CLI and function that checks fleet status-log lines against tasks/PING-SPEC.md.

Line format: `YYYY-MM-DD HH:MM | <job-id> | start|ok|fail|stalled|empty | <note>`
Checks:
1. A valid date and 24h time.
2. job-id is lowercase kebab-case.
3. The status is one of the five allowed values.
4. The note is 10 words or fewer.
5. The note has no `$` and no digits-with-currency pattern.
6. A configurable denylist of names (a file passed with `--denylist`) is matched case-insensitively.

CLI: `python -m statuslog.validate <file> [--denylist names.txt]`. It prints `line N: <reason>` for each bad line and exits 1 if any line is bad, 0 if all are good.

Tests: pytest in `src/statuslog/test_validate.py`, at least 12 cases (each rule passing and failing, empty file, trailing whitespace). Use only invented fixture data.
Done when `pytest -q` passes and a PR `codex/001-status-log-validator` is open with the result.
