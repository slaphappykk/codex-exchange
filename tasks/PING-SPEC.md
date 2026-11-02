# Status ping spec (Kris, 29 Oct 2026) — low overhead
Every scheduled/recurring job appends ONE line to /workspace/watchdog/status.log when it finishes (and at start if it runs longer than 30 min):
YYYY-MM-DD HH:MM | <job-id> | start|ok|fail|stalled|empty | <max 10 words, no client names or $>
No full logs. Silence in Slack/chat when healthy. Long jobs (nightly packs) also keep a heartbeat in their own run.log.
Watchdog reads only status.log lines newer than its cursor, compares to registry.md expected times + grace, and reports only late/stalled/failed/empty.
Report format to Sparky, one line per item: <job> | expected <time> | got <status/none> | <evidence path> | NEEDS KRIS (only if a human gate)
