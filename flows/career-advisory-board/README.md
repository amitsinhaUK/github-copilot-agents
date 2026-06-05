# Career Advisory Board

An AI "advisory board" of personas that deliberate a problem or document and return a consensus position.

## Run it
1. Open Copilot Chat in **Agent mode**.
2. Type `/` → pick **Career Advisory Board** (`/career-advisory-board`).
3. Provide a problem statement / question, or reference a document with `#file`.

The Chair runs four phases: independent position papers → side-by-side comparison → debate → final consensus (with dissent noted). Each member writes full-paragraph sections in their own authentic voice.

## Board members
Each is a standalone agent in `agents/` and can also be invoked solo from the agent picker:

| Agent | Lens they bring |
|-------|-----------------|
| Bill Gates | Long-term systems thinking, data, global scale |
| Satya Nadella | Empathy, growth mindset, platform/ecosystem |
| Charles Lamanna | Ship fast, AI agents/low-code, business ROI |
| Jeff Bezos | Customer obsession, working backwards, decision velocity |
| Julie Sweet | Enterprise reinvention, talent, responsible execution |
| Paul Daugherty | Applied emerging tech, human+machine, responsible AI |
| Jason Derulo | Brand, audience, virality, creator economy |

> These are simulations of public figures for deliberation purposes, not the real individuals.

## Layout
```
career-advisory-board/
  agents/    # one *.agent.md per board member
  prompts/
    career-advisory-board.prompt.md   # the orchestrator command
  README.md
```
