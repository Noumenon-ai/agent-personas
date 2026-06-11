# Agent Personas

**41 battle-tested AI agent personality templates.**

For anyone building multi-agent systems with CrewAI, AutoGen,
LangGraph, Claude, or raw LLM calls.

Copy a persona. Paste into your agent's system prompt. Done.

## Categories

- **Coding** (7 personas) — speed_builder, architect, security_auditor, minimalist, debugger, code_reviewer, devops
- **Business** (6 personas) — market_analyst, revenue_designer, copywriter, growth_hacker, customer_advocate, legal_advisor
- **Trading** (7 personas) — value_investor, contrarian, growth_investor, quant, momentum_trader, risk_manager, bull_bear_pair
- **Security** (6 personas) — red_teamer, blue_teamer, osint_analyst, threat_hunter, forensics, social_engineer
- **Research** (5 personas) — deep_researcher, fact_checker, competitive_intel, trend_spotter, devil_advocate
- **Creative** (5 personas) — visual_designer, brand_strategist, content_creator, ux_writer, art_director
- **Meta** (5 personas) — observer, mediator, project_manager, quality_gate, retrospective
- **Templates** (2 files) — blank persona template, debate format guide

## Quick Start

```bash
# Clone the repo
git clone https://github.com/noumenon-ai/agent-personas.git

# Use a persona
cat agent-personas/coding/speed_builder.md
# Copy the Personality section into your agent's system prompt
```

## Usage

These are framework-agnostic markdown system prompts. There is no SDK
and no integration layer: you read the file and pass its contents to
your framework's system-prompt (or backstory) parameter. Works with any LLM.

### With CrewAI
```python
from crewai import Agent

speed_builder = Agent(
    role="Speed Builder",
    goal="Ship working code as fast as possible",
    backstory=open("coding/speed_builder.md").read(),
)
```

### With AutoGen (AgentChat)
```python
from autogen_agentchat.agents import AssistantAgent
from autogen_ext.models.openai import OpenAIChatCompletionClient

architect = AssistantAgent(
    name="architect",
    model_client=OpenAIChatCompletionClient(model="gpt-4o"),
    system_message=open("coding/architect.md").read(),
)
```

### With LangGraph
```python
# The persona file is the system message for your agent node
system_prompt = open("coding/architect.md").read()
```

### With raw API calls
```python
messages = [
    {"role": "system", "content": open("security/red_teamer.md").read()},
    {"role": "user", "content": "Audit this authentication flow..."},
]
```

## Multi-Agent Debates

See [templates/DEBATE_FORMAT.md](templates/DEBATE_FORMAT.md) for how to
structure productive debates between agents.

## Contributing

Built a great persona? PR it. Include: name, role, personality,
pitch format, debate rules, weakness.

## License

MIT

---

Part of the NOUMENON ecosystem.
NOUMENON uses 17 specialized agents that debate before building.
These templates are simplified, generic versions — useful starting points
for your own multi-agent systems.
---
Built by [Noumenon](https://github.com/Noumenon-ai)