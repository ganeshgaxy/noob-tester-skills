# noob-visual

Execute ONE pre-claimed visual test case (BDD/traditional format with visual_steps config). Baseline mode captures screenshots, verification mode does pixel-by-pixel diffs. Includes trace, profiler, console, and error collection.

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-visual
```

## Usage

```
/noob-visual
```

Executes one pre-claimed visual test case per invocation. Use `noob-visual-claim` first to create/resume a visual run and claim the next entry. Pass `$CLAIM` and `$VISUAL_RUN_ID` to this skill.
