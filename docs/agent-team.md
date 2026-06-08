# Agent team

Summary of the custom agent team used to build Mona's Project Pulse dashboard.

- Orchestrator — model: Claude Opus 4.7 (copilot). Responsibility: coordinates Planner, Coder, and Designer; breaks requests into phases, assigns file scopes, and verifies integrated results. Definition: .github/agents/orchestrator.agent.md

- Planner — model: Claude Opus 4.7 (copilot). Responsibility: research, produce ordered implementation plans with file assignments, dependencies, edge cases, and validation expectations. Definition: .github/agents/planner.agent.md

- Coder — model: GPT-5.5 (copilot). Responsibility: implement code, fix bugs, create runnable app support and validate behavior within assigned file scope. Definition: .github/agents/coder.agent.md

- Designer — model: Gemini 3.1 Pro (copilot). Responsibility: UI/UX, accessibility, interaction flow, and visual design for a polished, responsive Project Pulse dashboard. Definition: .github/agents/designer.agent.md

Note: Work is orchestrated from the GitHub Copilot CLI running in a Codespace.