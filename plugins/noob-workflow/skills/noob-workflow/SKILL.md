---
name: noob-workflow
description: Register a new ticket ID into the ticket_workflow table and set it up for processing. Run this first when a ticket enters the QA pool. Creates the canonical workflow record that all other skills (analyze, plan, test) track against.
---

# Ticket Workflow Setup

Register a ticket ID in the workflow system so its full lifecycle can be tracked — from `new` through `running` to `completed`.

## Usage

```bash
# /noob-workflow <TICKET-ID>
```

## Steps

### 1. Check if ticket is already registered

```bash
EXISTING=$(noob-tester ticket-workflow get <TICKET-ID> --json 2>/dev/null)
STATUS=$(echo "$EXISTING" | jq -r '.status // empty')
```

If `STATUS` is non-empty, the ticket already exists. Skip to step 3 to report current state instead of re-adding.

### 2. Register the ticket

```bash
RESULT=$(noob-tester ticket-workflow add <TICKET-ID> --json)
echo "$RESULT"
```

This creates a row with:
- `status: new`
- `progress: 0`
- `active: 0`
- `added_at`: current timestamp

### 3. Confirm and report state

```bash
SUMMARY=$(noob-tester ticket-workflow get <TICKET-ID> --json)
echo "$SUMMARY"
```

Report back:
- `ticket_id`
- `status`
- `added_at`
- Any pre-existing linked data: `run_count`, `analysis_count`, `plan_count`, `test_case_count`, `issue_count`, `blocker_count`

## Output

On success, output the full workflow summary JSON so the caller knows:
1. Whether this was a new registration or an existing ticket
2. What linked data already exists for this ticket (runs, analyses, test cases, etc.)
3. The current status so downstream skills know where to pick up

## Example output

```json
{
  "ticket_id": "PROJ-123",
  "status": "new",
  "current_phase": null,
  "progress": 0,
  "active": 0,
  "added_at": "2026-05-18 10:00:00",
  "run_count": 0,
  "analysis_count": 0,
  "plan_count": 0,
  "test_case_count": 0,
  "visual_test_case_count": 0,
  "blocker_count": 0,
  "issue_count": 0
}
```

## Notes

- Ticket ID is always uppercased automatically (e.g. `proj-123` → `PROJ-123`)
- If the ticket already exists, `upsertTicketWorkflow` is idempotent — it will not overwrite an existing status
- This skill only registers the ticket. Transitioning to `queued` or `running` is done by the orchestrator or polling agent once work begins
- To update status later: `noob-tester ticket-workflow transition <TICKET-ID> --status queued`
