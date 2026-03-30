# noob-ticket-cache

Fetch and cache all ticket context (Jira, Confluence) using cache-first pattern. Run before any skill that needs ticket data.

## Installation

```bash
claude plugin install noob-ticket-cache@noob-tester-skills
```

## Usage

```
/noob-ticket-cache <TICKET-ID>
```

Fetches and caches all ticket context in one pass — ticket info, remote links, comments, parent/grandparent hierarchy, sibling tickets, and linked Confluence pages. Other skills call this first instead of fetching individually.
