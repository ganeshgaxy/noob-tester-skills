# noob-repos-setup

Validate, clone, sync, and index a user-provided SSH repo URL for a ticket.

## Installation

```bash
claude plugin install noob-repos-setup@noob-tester-skills
```

## Usage

```
/noob-repos-setup <TICKET-ID> --url <ssh-repo-url> [--branch <source-branch>]
```

Validates the SSH URL, runs `setup-for-ticket` to discover, clone, sync, and index the repo so codebase search works for downstream skills.
