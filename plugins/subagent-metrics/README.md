# subagent-metrics

A Claude Code hook plugin that automatically captures subagent execution metrics and logs them to [noob-tester](https://github.com/ganeshgaxy/noob-tester) sessions.

## What It Does

When a Claude Code subagent finishes (`SubagentStop` event), this hook:

1. Reads the agent's transcript file
2. Extracts the noob-tester session ID from the agent's last message (UUID pattern)
3. Parses token usage (input, output, cache read, cache create)
4. Counts tool invocations
5. Calculates execution duration
6. Detects the model used
7. Logs everything to noob-tester via `noob-tester metrics log`

## Metrics Captured

| Metric | Description |
|--------|-------------|
| Input tokens | Total input tokens across all assistant turns |
| Output tokens | Total output tokens across all assistant turns |
| Cache read tokens | Tokens served from cache |
| Cache create tokens | Tokens written to cache |
| Tool calls | Total number of tool_use blocks |
| Duration | Wall-clock time from first to last transcript entry (ms) |
| Model | Model ID from the first assistant message |

## Prerequisites

- [noob-tester](https://github.com/ganeshgaxy/noob-tester) CLI installed and available on `PATH`
- `jq` for JSON parsing
- `python3` for duration calculation (optional — duration defaults to 0 if unavailable)

## Installation

```bash
claude plugin marketplace add ganeshgaxy/noob-tester-skills
claude plugin install subagent-metrics@noob-tester-skills
```

## How It Works

The hook fires on `SubagentStop` and reads the JSON payload from stdin, which includes:

- `agent_transcript_path` — path to the subagent's full transcript
- `last_assistant_message` — the agent's final response

It scans the last message for a UUID (the noob-tester session ID). If found, it aggregates metrics from the transcript and calls:

```bash
noob-tester metrics log <session-id> \
  --input-tokens <n> \
  --output-tokens <n> \
  --cache-read-tokens <n> \
  --cache-create-tokens <n> \
  --tools <n> \
  --duration <ms> \
  --model <model-id> \
  --actions 1
```

If no session ID is found in the message, the hook exits silently.
