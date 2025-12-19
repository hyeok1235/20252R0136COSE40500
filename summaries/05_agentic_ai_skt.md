# Agentic AI in SK Telecom

**Topic:** AI Agents, Korean LLM Development

## AI Evolution Spectrum

| Level | Description |
|-------|-------------|
| **AI** | Response based on training data, limited external tool usage |
| **AI Workflow** | Executes predefined flows, can connect external AI/tools |
| **AI Agent** | Self-plans external resource usage, iterative self-reflection |

**Key insight:** An agent doesn't need to take physical actions—self-planning and executing user queries qualifies as agentic behavior.

## Industry Landscape

- **Big Tech (Google, OpenAI):** Broad focus on general services; vulnerable to vertical-specific competitors
- **OpenAI's strategy:** Targeting Google by building semiconductors and servers
- **Regulation gap:** Commercial validation prioritized over downsides; IP concerns (e.g., Ghibli) have limited recourse

## A.X. 4.0 (SKT's Model)

**Key Innovation:** Korean-specialized tokenizer

**Challenge:** Changing tokenizer completely alters the first layer

**Solution:** Continual pretraining—preserves reasoning ability while changing embedding space

## Agentic AI Platforms

| Platform | Issue |
|----------|-------|
| ChatGPT | Removed model selection, caused controversy |
| OpenAI Agent Builder | Too complex for developers |
| Gemini Agent Builder | Too simple, reduces trust |

**Observation:** Even big tech is struggling with agent UX design

## Research Directions

1. **Training perspective:** Focus on model and performance
2. **Test-time perspective:** Focus on workflow optimization
3. **Agentic RL:** Research on "environments" for agent training
4. **Agent Design Patterns:** Single vs multi-agent, modular composition, operational efficiency
5. **Memory management:** What to store, memory structure design—still much work needed

## Conclusions

Agentic AI represents a shift from static responses to self-planning systems. SKT's approach emphasizes Korean language optimization through novel continual pretraining, while the industry continues exploring optimal agent architectures.
