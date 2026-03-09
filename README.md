# Prompt Optimization Framework v2.0

A systematic framework for evaluating, optimizing, and iterating on prompts. Built on two comprehensive research surveys covering 1,500+ papers and 58+ prompting techniques.

## What This Is

A structured methodology for prompt engineering that replaces trial-and-error with a repeatable five-step process: Assess, Diagnose, Optimize, Validate, Test. It works for any LLM, any task type, and any complexity level.

## Research Foundation

- **["The Prompt Report: A Systematic Survey of Prompting Techniques"](https://arxiv.org/abs/2406.06608)** (Schulhoff et al., 2024, updated Feb 2025). 1,500+ papers. 58 techniques cataloged. Primary source for the core taxonomy.
- **["A Systematic Survey of Prompt Engineering in Large Language Models"](https://arxiv.org/abs/2402.07927)** (Sahoo et al., 2024, updated March 2025). 41+ techniques by application domain. Source for Chain-of-Draft, Graph-of-Thoughts, Thread-of-Thought, Logic-of-Thought, ReAct, ECHO, Code Prompting, System 2 Attention.

## Files

| File | Description |
|------|-------------|
| `system-prompt-v2.md` | The system prompt. Copy-paste into Claude Projects or any LLM as a custom instruction. |
| `prompt-optimization-framework.md` | Full framework documentation with technique details, examples, and evaluation checklist. |
| `README.md` | This file. |

## How to Use

1. Copy the contents of `system-prompt-v2.md` into your LLM of choice as a system prompt or custom instruction
2. Paste any prompt you want to optimize
3. The framework runs the five-step process automatically: Assessment, Diagnosis, Optimized Prompt, Rationale, Testing Plan

## Technique Coverage (v2.0)

### In-Context Learning
- Zero-Shot, Few-Shot (2-8 exemplars), exemplar ordering and selection

### Thought Generation
- Chain-of-Thought (Zero-Shot, Few-Shot)
- Chain-of-Draft (minimalist reasoning, 7-8x shorter chains)
- Step-Back Prompting
- Plan-and-Solve

### Decomposition
- Least-to-Most
- Tree-of-Thought (parallel reasoning paths)
- Graph-of-Thoughts (non-linear reasoning with branch merging)

### Reasoning with Action
- ReAct (alternating thinking and tool use, foundation of agentic AI)

### Self-Criticism
- Self-Refine (iterative improvement)
- Chain-of-Verification (verification questions)
- Self-Consistency (multiple paths, majority vote)
- Self-Harmonized CoT / ECHO (automated diverse chain unification)

### Context Management
- Thread-of-Thought (chaotic/long context processing, 47% improvement)
- System 2 Attention (context filtering, 80.3% accuracy on factual QA)

### Logic Verification
- Logic-of-Thought (formal logic extraction, 4.35% improvement)

### Code Reformulation
- Code Prompting (8.42 F1 improvement on conditional reasoning)

### Prompt Optimization
- Automatic Prompt Engineer (APE)
- Rephrase and Respond (RaR)

## How I Use This

- **OpenClaw Agent Development:** Designing identity files, guardrails, and operational rules for an autonomous AI agent
- **Customer Intelligence Engine:** Optimizing classification prompts processing feedback from 6 sources
- **AI Trust Layer:** Structuring adversarial test cases, output grading rubrics, and approval gate prompts
- **AI Maturity Assessments:** Consistent, auditable analysis prompts across 20+ sources
- **Enterprise Prompt Libraries:** Built at Agile Directive using this methodology

## Changelog

### v2.0 (March 2026)
- Added 9 techniques from Sahoo et al. 2025 survey
- Added quantitative results from research (Self-Consistency +17.9%, ThoT +47%, S2A 80.3%, LoT +4.35%)
- Added second research paper citation
- Added ReAct for agentic AI workflows
- Added common failure modes section (noisy context, unfaithful reasoning, irrelevant context contamination)
- Restructured technique sections with "When to Use" framing

### v1.0 (March 2026)
- Initial release based on Schulhoff et al. 2024

## Author

Angel Torres | [Portfolio](https://axiomatic-second-9fc.notion.site/AI-Product-Management-Portfolio-312817fd0f37809bbe05e51aba6a6fd9) | [LinkedIn](https://www.linkedin.com/in/angel-torres-4122281) | [GitHub](https://github.com/Angeldtorres-tech)
