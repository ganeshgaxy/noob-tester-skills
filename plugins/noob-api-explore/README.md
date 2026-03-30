# noob-api-explore

Execute ALL api-layer test cases in one invocation using curl/jq. Reads codebase once, authenticates per role, loops through every API test, validates responses, cleans up.

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-api-explore
```

## Usage

```
/noob-api-explore
```

Runs all API layer test cases in a single invocation — authenticates once, loops through every test, validates responses, and cleans up created resources.
