# Prompt Optimization Framework

A systematic framework for evaluating, optimizing, and iterating on prompts, grounded in research from "The Prompt Report: A Systematic Survey of Prompting Techniques" and Anthropic's Claude guidelines.

## What This Is

A structured methodology for prompt engineering that goes beyond trial-and-error. It applies research-backed techniques to systematically improve prompt quality, reliability, and performance.

## Core Components

### Analysis Framework
- **Core Components Assessment:** Evaluates prompts across 7 essential elements (directive, role, context, examples, output format, style, reasoning guidance)
- **Technique Selection:** Maps tasks to optimal prompting techniques from the research taxonomy
- **Best Practices Checklist:** Claude-specific optimizations and general prompt engineering principles
- **Issue Detection:** Identifies ambiguity, sensitivity, security vulnerabilities, and alignment gaps

### Technique Taxonomy
- **In-Context Learning (ICL):** Zero-shot, few-shot (2-8 exemplars), exemplar ordering and selection
- **Thought Generation:** Chain-of-Thought, Step-Back Prompting, Plan-and-Solve
- **Decomposition:** Least-to-Most, Tree-of-Thought, Recursion-of-Thought
- **Self-Criticism:** Self-Refine, Chain-of-Verification, Self-Calibration
- **Ensembling:** Self-Consistency, DENSE, Meta-CoT

### Optimization Process
1. **Initial Assessment:** Task type, components present/missing, applicable techniques
2. **Technique Recommendations:** Research-backed improvements with expected impact
3. **Optimized Prompt:** Restructured version with annotations
4. **Rationale:** Why each change improves performance, trade-offs considered
5. **Testing Guidance:** Validation approach and failure mode testing

## How I Use This

This framework drives my daily AI work:

- **OpenClaw Agent Development:** Designing and refining the identity files, guardrails, and operational rules that govern an autonomous AI agent
- **Customer Intelligence Engine:** Optimizing classification prompts that process feedback from 6 sources with 92.4% accuracy
- **AI Maturity Assessments:** Structuring prompts for consistent, auditable analysis across 20+ sources
- **Prompt Library Development:** Built enterprise prompt libraries at Agile Directive using this methodology

## Key Research References

- "The Prompt Report: A Systematic Survey of Prompting Techniques" (2024)
- "Who Validates the Validators?" (Three Gulfs framework)
- Anthropic Claude documentation and best practices
- Aakash Gupta + Hamel Husain: AI Evals for PMs (AMI Cycle)

## Author

Angel Torres | [Portfolio](https://axiomatic-second-9fc.notion.site/AI-Product-Management-Portfolio-312817fd0f37809bbe05e51aba6a6fd9) | [LinkedIn](https://linkedin.com/in/angel-torres-4122281) | [GitHub](https://github.com/Angeldtorres-tech)
