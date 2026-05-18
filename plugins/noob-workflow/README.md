# noob-workflow

Register a new ticket ID into the ticket_workflow table and set it up for processing. Run this first when a ticket enters the QA pool. Creates the canonical workflow record that all other skills (analyze, plan, test) track against.

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-workflow
```

## Usage

```
/noob-workflow
```

Creates the canonical workflow record for a ticket, which all downstream skills (noob-analyze, noob-plan, noob-testcase, etc.) track against.
