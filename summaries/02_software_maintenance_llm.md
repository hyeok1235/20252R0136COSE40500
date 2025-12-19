# Rethinking Software Maintenance with Large Language Models

**Research Area:** Software Engineering (Automated Developing & Debugging)

**Lab:** SELENE Research Lab

## Key Contributions

- Introduces AutoFL: LLM-based automated fault localization
- Addresses debugging bottleneck through automation
- Works across multiple programming languages (Java, Python)
- Overcomes LLM context length limitations via function-calling navigation

## Background

Software Engineering extends beyond coding to include design, management, and maintenance. As complexity increases, maintenance becomes increasingly difficult.

## Methodology: AutoFL

Uses LLMs with function-calling navigation to selectively explore relevant code sections without ingesting entire codebases.

## Strengths

1. **Automates debugging bottleneck** - Reduces manual tracing through codebases, logs, and error outputs
2. **Multi-language support** - Leverages LLMs trained on diverse programming data
3. **Scalable design** - Function-calling navigation handles large repositories exceeding LLM context limits

## Weaknesses

1. **Static knowledge** - Cannot incorporate latest library updates, APIs, or evolving practices
2. **Domain limitations** - May struggle with niche areas (HPC, embedded systems, proprietary frameworks)
3. **Privacy concerns** - Analyzing proprietary code via external APIs raises IP and compliance issues

## Possible Improvements

1. **Multi-agent systems** - Specialized agents for logs, dependencies, and fix evaluation
2. **External context** - Incorporate bug reports, issue discussions, commit histories
3. **Dynamic analysis** - Combine static navigation with runtime behavior analysis (exception traces, performance, I/O)

## Conclusions

AutoFL demonstrates LLMs can effectively automate fault localization across languages, though challenges remain in handling dynamic environments, specialized domains, and privacy concerns.
