# College Admissions Advisor

A research-backed admissions advisor for guardians/parents of US students. It does deep internet research on a target university, honestly evaluates the student's idea, and returns an age-appropriate roadmap with real, sourced examples.

## Run it
1. Open Copilot Chat in **Agent mode**.
2. Type `/` → pick **College Admissions Advisor** (`/college-admissions-advisor`).
3. Provide the **target university**, the **student's idea / intended major / activity**, and any context (age, interests, constraints). You can also reference a document with `#file`.

The advisor runs three phases: deep university research → honest evaluation of the idea (strengthen if good, replace if weak) → a synthesized, grade-by-grade roadmap with real examples.

## What it does
- **Researches the specific school** — what it values, representative admit profile, deadlines/test policy, and distinctive opportunities — using live web sources, with citations.
- **Evaluates the student's proposal** against *that* school's priorities:
  - **Strong idea** → keeps it and adds tangential extensions to turn it into a genuine "spike."
  - **Weak idea** → says so honestly and offers better alternatives that fit the student's real interests.
  - **Mixed** → keeps the strong core, fixes the gaps.
- **Surfaces real internet examples** relevant to the target school (admit stories, projects, programs, competitions), each with its source link.
- **Returns a staged roadmap** tuned to a long runway (built for ~13-year-olds), prioritizing depth, authenticity, and wellbeing over résumé-stuffing.

## Agents
Each is a standalone agent in `agents/` (shown in the picker under its namespaced name):

| Agent (picker name) | Role |
|---|---|
| College Advisor: University Researcher | Deep, source-backed research on the target school |
| College Advisor: Proposal Evaluator | Honest strength rating; strengthen, refine, or replace the idea |
| College Advisor: Admissions Advisor | Synthesizes research + evaluation into the final roadmap |

> **Naming convention:** agent/prompt `name:` fields are a **global namespace** in VS Code, even though files live in per-flow folders. Every agent here is prefixed with `College Advisor:` so it never collides with another flow. Apply a unique `<Flow>:` prefix to each new flow's agent names.

## Important notes
- **No guarantees.** Admissions is probabilistic; this tool improves odds and builds genuine capability — it never promises a result.
- **Verify time-sensitive facts.** Acceptance rates, deadlines, and test policies change yearly; confirm on the school's official site.
- **Privacy.** Avoid sharing unnecessary identifying details about minors.

## Layout
```
college-admissions-advisor/
  agents/    # university-researcher, proposal-evaluator, admissions-advisor
  prompts/
    college-admissions-advisor.prompt.md   # the orchestrator command
  README.md
```
