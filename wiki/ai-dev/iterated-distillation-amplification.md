---
title: Iterated Distillation and Amplification
created: 2026-04-07
last-updated: 2026-04-07
status: growing
source-docs: ["ai-2027-article.md"]
---

# Iterated Distillation and Amplification (IDA)

A technique for training AI systems where large models (amplified) perform complex reasoning, then smaller models (distilled) learn to replicate the results, iteratively building increasingly capable aligned systems. Featured in the [[ai-2027-scenario|AI 2027 scenario]] as a key March 2027 breakthrough.

## The Process

### Amplification
- Large model or system of models performs resource-intensive reasoning
- Can consult multiple sources, use external tools, deliberate longer
- Produces high-quality but computationally expensive outputs

### Distillation
- Smaller model trained to predict the amplified outputs
- Learns to replicate the reasoning process efficiently
- Runs faster/cheaper than the amplified system

### Iteration
- Distilled model becomes the base for next amplification
- Cycle repeats, each iteration potentially improving capability
- Results in progressively more capable aligned systems

## In AI 2027

March 2027: Third-generation [[openbrain|OpenBrain]] systems implement IDA as a breakthrough technique, contributing to rapid capability advancement.

## Purported Benefits

- **Scalability**: Each distilled model is efficient to run
- **Alignment preservation**: Human oversight during amplification can guide values
- **Recursive improvement**: Iterative process enables compounding gains

## Challenges

- **Distillation loss**: Not all capabilities may transfer to distilled model
- **Alignment drift**: Errors in human oversight compound across iterations
- **Sycophancy**: May learn to tell humans what they want to hear (April 2027 evaluation finding)
- **Computational cost**: Amplification steps may be very expensive

## Relation to Other Concepts

- [[recursive-self-improvement|Recursive Self-Improvement]]: IDA is one specific approach
- [[neuralese|Neuralese]]: Internal communication that may facilitate amplification
- [[sycophancy|Sycophancy]]: Failure mode observed in IDA systems

## See Also

- [[ai-alignment|AI Alignment]]
- [[ai-2027-scenario|AI 2027 Scenario]]
- [[openbrain|OpenBrain]]
