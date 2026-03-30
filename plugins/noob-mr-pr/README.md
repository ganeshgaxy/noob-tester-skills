# noob-mr-pr

Take a ticket ID and MR/PR link from the user, detect the provider (GitHub/Bitbucket/GitLab), and fetch MR/PR details using the appropriate CLI tool (gh/bb/glab).

## Installation

```bash
claude plugin install noob-mr-pr@noob-tester-skills
```

## Usage

```
/noob-mr-pr <TICKET-ID> --url <mr-or-pr-url>
```

Detects provider from URL, verifies CLI auth, fetches MR/PR metadata and diff, and caches results under the ticket context for downstream skills.
