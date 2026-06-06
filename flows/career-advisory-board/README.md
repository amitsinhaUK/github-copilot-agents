# Career Advisory Board

An AI "advisory board" of personas that deliberate a problem or document and return a consensus position.

## Run it
1. Open Copilot Chat in **Agent mode**.
2. Type `/` → pick **Career Advisory Board** (`/career-advisory-board`).
3. Provide a problem statement / question, or reference a document with `#file`.

The Chair runs four phases: independent position papers → side-by-side comparison → debate → final consensus (with dissent noted). Each member writes full-paragraph sections in their own authentic voice.

## Board members
Each is a standalone agent in `agents/` and can also be invoked solo from the agent picker (shown there under its namespaced name, e.g. **Career Board: Bill Gates**):

| Agent (picker name) | Lens they bring |
|-------|-----------------|
| Career Board: Bill Gates | Long-term systems thinking, data, global scale |
| Career Board: Satya Nadella | Empathy, growth mindset, platform/ecosystem |
| Career Board: Charles Lamanna | Ship fast, AI agents/low-code, business ROI |
| Career Board: Jeff Bezos | Customer obsession, working backwards, decision velocity |
| Career Board: Julie Sweet | Enterprise reinvention, talent, responsible execution |
| Career Board: Paul Daugherty | Applied emerging tech, human+machine, responsible AI |
| Career Board: Jason Derulo | Brand, audience, virality, creator economy |

> These are simulations of public figures for deliberation purposes, not the real individuals.

> **Naming convention:** agent/prompt `name:` fields are a **global namespace** in VS Code, even though files live in per-flow folders. Every agent here is prefixed with `Career Board:` so multiple flows can reuse the same persona (e.g. another flow's own “Bill Gates”) without colliding. Apply a unique `<Flow>:` prefix to each new flow's agent names.

## Referee
A neutral **Argument Evaluator** (`agents/argument-evaluator.agent.md`, picker name **Career Board: Argument Evaluator**) checks every argument against the question in hand. It holds no opinion on the answer — it only judges relevance and grounding:

- **ALLOW** — the argument is on-topic (including merely *tangential* arguments) and grounded → debate continues.
- **ALLOW WITH FLAG** — relevant but contains a specific unsupported/fabricated claim → continues, but no one may build on the flagged claim.
- **STOP** — the argument is *entirely irrelevant to the question and/or hallucinated* → it is shown (it was already made) but halted: not rebutted, not extended, and excluded from the final synthesis.

The bar for `STOP` is intentionally high, so tangentially relevant arguments are allowed to play out.

## Layout
```
career-advisory-board/
  agents/    # one *.agent.md per board member, plus argument-evaluator.agent.md (referee)
  prompts/
    career-advisory-board.prompt.md   # the orchestrator command
  README.md
```
