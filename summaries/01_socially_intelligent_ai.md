# Towards Socially-Intelligent AI: Modeling Human Social Interactions

**Research Areas:** Self-Supervised Learning, Multimodal Learning, Social AI

## Key Contributions

- Proposes a path toward AI with social intelligence (눈치)
- Introduces 3 new multimodal social benchmarks
- Addresses limitations of text-only approaches for social understanding

## Core Concept

**Socially-Intelligent AI = Social Perception + Social Robotics**

Social interactions involve:
- Social actions & conversation dynamics
- Social relationships
- Emotion & sentiment
- Intentions & goals
- Non-verbal actions (beyond speech)
- Multi-party conversations

## Methodology

### 1. Multimodal Social Interactions
- Extract multi-party dynamics from multimodal cues
- Text alone is insufficient; requires visual, audio, and contextual data
- Challenge: Densely aligned representations needed to avoid blending individual features

### 2. Gesture Understanding
- Previous datasets: single-person, lab environments, task-specific
- New benchmark: multi-person settings with relationship understanding

### 3. Gaze Understanding
- Goal: Build better gaze estimators
- Previous approaches: Complex models with depth, pose, eyes (auxiliary models)
- Finding: Foundation models alone are insufficient; can even degrade performance

## Future Directions

**Challenges for human-level social AI:**

1. **ML aspects:** Need unified framework; current MLLMs cannot handle fine-grained social data
2. **Social domain aspects:** Missing beliefs about others and shared beliefs among conversation participants

## Conclusions

Developing socially-intelligent AI requires multimodal understanding beyond language, with consideration of implicit social dynamics and shared mental states.
