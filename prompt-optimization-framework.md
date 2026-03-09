# Prompt Optimization Framework

**Author:** Angel Torres | Alinea Consulting
**Version:** 1.0 | March 2026

## The Problem

Most people write prompts the way they write emails: stream of consciousness, vague instructions, hope for the best. When the output is wrong, they tweak a word and try again. There is no systematic method for diagnosing why a prompt failed or how to fix it.

This framework changes that. It provides a repeatable system for evaluating any prompt against research-backed criteria, identifying what is missing or broken, and applying specific techniques to fix it. It works for any LLM, any task type, and any complexity level.

I built this because prompt engineering shows up in every AI PM job description, but most "prompt engineering" in practice is just trial and error. This framework turns it into a structured discipline.

## Research Foundation

This framework is built on two comprehensive surveys of prompting techniques:

- **["The Prompt Report: A Systematic Survey of Prompting Techniques"](https://arxiv.org/abs/2406.06608)** (Schulhoff et al., 2024, updated Feb 2025). Surveyed 1,500+ research papers. Cataloged 58 distinct prompting techniques with effectiveness data across task types. The primary source for the core technique taxonomy in this framework.

- **["A Systematic Survey of Prompt Engineering in Large Language Models: Techniques and Applications"](https://arxiv.org/abs/2402.07927)** (Sahoo et al., 2024, updated March 2025). Covers 41+ techniques organized by application domain. Published in Springer's Frontiers of Computer Science. Source for newer techniques including Chain-of-Draft, Graph-of-Thoughts, Thread-of-Thought, Logic-of-Thought, Code Prompting, and System 2 Attention.

The technique taxonomy, component model, and best practices in this framework are drawn from both surveys and adapted into a practical evaluation system for AI product management.

## How It Works

The framework runs in five steps. Each step produces a concrete output.

**Step 1: Assess.** Identify what the prompt has and what it's missing. Every effective prompt needs a clear directive, relevant context, output format specification, and reasoning guidance. Most prompts are missing at least two of these.

**Step 2: Diagnose.** Match the task type to the right technique. A classification task needs few-shot examples. A reasoning task needs chain-of-thought. A complex multi-step task needs decomposition. The wrong technique for the task type is why most prompts underperform.

**Step 3: Optimize.** Restructure the prompt using the recommended techniques. Add what's missing. Remove what's creating ambiguity. Reorder examples (ordering alone can swing accuracy by 40+ points in research studies).

**Step 4: Validate.** Explain every change and why it should improve performance. Document trade-offs (added complexity vs. clarity, token usage vs. accuracy). No change without a rationale.

**Step 5: Test.** Define how to verify the optimized prompt works. Specify what to test, what failure modes to watch for, and how to compare against the baseline.

## Core Components

Every prompt is evaluated against seven components. If any required component is missing, that's the first fix.

| Component | What It Does | When You Need It |
|-----------|-------------|-----------------|
| Directive | The core instruction. What you want the model to do. | Always |
| Role/Persona | An assigned identity that shapes the response style and expertise level. | When domain expertise or a specific perspective improves the output |
| Context | Background information the model needs to produce a good answer. | Almost always. Models cannot infer what you don't provide. |
| Examples | Demonstrations of the task with correct outputs. | When you need the model to follow a specific pattern or format |
| Output Format | Explicit specification of how the response should be structured. | Always. Unspecified format produces inconsistent results. |
| Style Instructions | Tone, length, vocabulary, or formatting constraints. | When the default style doesn't match the use case |
| Reasoning Guidance | Instructions for how to think through the problem. | For any task involving logic, math, analysis, or multi-step reasoning |

## Technique Selection

The framework maps task types to specific, research-backed prompting techniques. Selecting the right technique matters more than wordsmithing.

### When to Use Few-Shot Learning

Give the model 2-8 examples of the task with correct outputs. Use this when the task follows a pattern (classification, extraction, formatting, translation between formats).

Key details that most people miss:
- Example quality matters more than quantity. One good example beats five mediocre ones.
- Example ordering affects accuracy significantly. Research shows 40+ point swings from reordering alone.
- Include edge cases. If you only show easy examples, the model handles easy cases well and fails on hard ones.
- Balance your labels. If 7 of 8 examples have the same label, the model is biased toward that label.

### When to Use Chain-of-Thought

Add "Let's think step by step" or include examples that show the reasoning process, not just the answer. Use this for any task involving reasoning: math, logic, analysis, comparison, evaluation.

Variants:
- **Zero-shot CoT:** Just add "Let's think step by step." Simple and surprisingly effective.
- **Few-shot CoT:** Provide examples that include the reasoning chain, not just the input and output. More work to set up, better results.
- **Plan-and-Solve:** "Devise a plan, then solve step by step." Forces the model to organize before executing.
- **Step-Back Prompting:** Ask a high-level question first, then use that answer to inform the detailed response.

### When to Use Chain-of-Draft

A lighter version of Chain-of-Thought. Each reasoning step is as short as possible: just enough to capture the key insight, not a full explanation. Use this when you need reasoning but token cost or latency matters.

CoD produces reasoning chains that are 7-8x shorter than CoT while maintaining comparable accuracy. It works because most intermediate reasoning steps contain filler language that doesn't contribute to the answer. Stripping that filler forces the model to focus on what actually matters at each step.

Best for: math, logic, any task where CoT works but the verbose reasoning is unnecessary.

### When to Use Decomposition

Break a complex problem into smaller sub-problems and solve each one. Use this when a single prompt tries to do too many things at once.

- **Least-to-Most:** Start with the simplest sub-problem, use that answer to solve the next, build up to the full answer.
- **Tree-of-Thought:** Explore multiple reasoning paths in parallel, then select the best one.
- **Graph-of-Thoughts:** Like Tree-of-Thought but allows merging insights from different branches. Human thinking is not a tree. It's a graph: ideas connect, combine, and loop back. GoT improved accuracy by 5.08% over CoT on math reasoning with T5-large.

### When to Use Reasoning with Action (ReAct)

The model alternates between thinking and acting. A reasoning step ("I need to find the current price") is followed by an action step (search the web, query a database, call an API), then the model reasons about the result before deciding the next action.

This is the foundation of agentic AI. Any system where an LLM needs to use tools, access external data, or take actions in the real world builds on ReAct. It reduces hallucination because the model grounds its reasoning in real retrieved data rather than generating from memory alone.

Best for: research tasks, fact-checking, any workflow that requires external data, agentic AI systems.

### When to Use Self-Criticism

Have the model evaluate and improve its own output. Use this when accuracy matters more than speed.

- **Self-Refine:** Generate an answer, critique it, then improve based on the critique. GPT-4 showed 8.7 point improvement in code optimization and 21.6 points in sentiment reversal using iterative self-refinement.
- **Chain-of-Verification:** Generate an answer, create verification questions, answer those questions, then revise if the verification reveals errors.
- **Self-Consistency:** Generate multiple answers using different reasoning paths, then select the most common conclusion. Improved accuracy by 17.9% on GSM8K math reasoning.
- **Self-Harmonized CoT (ECHO):** Automatically generates diverse reasoning chains, then unifies them into a coherent pattern. Outperformed Auto-CoT by 2.8% across 10 benchmarks while retaining performance with 50% fewer examples.

## Common Failure Modes

Before optimizing, check whether the prompt fails for one of these reasons:

**Ambiguity.** The instruction could be interpreted multiple ways. If you can read the prompt and imagine two different valid responses, it's ambiguous.

**Missing format specification.** The prompt says what to do but not how to structure the output. The model guesses, and its guess rarely matches what you wanted.

**Poor examples.** Examples that are too easy, too similar, inconsistently formatted, or incorrectly labeled. The model learns the wrong pattern.

**No reasoning guidance.** The prompt asks for a complex analysis but doesn't instruct the model to think through it. The model jumps to a conclusion instead of reasoning.

**Noisy or chaotic context.** The prompt includes a long, messy input (a meeting transcript, an email thread, a scraped web page) but doesn't tell the model how to process it. Thread-of-Thought (ThoT) addresses this: break the context into segments, analyze each one, then synthesize. Research showed 47% improvement on question answering in chaotic contexts.

**Unfaithful reasoning.** The model generates reasoning steps that look logical but the conclusion doesn't actually follow from them. Logic-of-Thought (LoT) addresses this by extracting formal logic from the prompt, extending it using propositional logic rules, and feeding the extended logic back into the prompt. Improved CoT accuracy by 4.35% on logical reasoning benchmarks.

**Prompt injection vulnerability.** User-provided input inside the prompt could override the instructions. This matters for any prompt that processes external content (emails, web pages, user messages, documents).

**Irrelevant context contamination.** The input contains information that is technically present but irrelevant to the task, and the model gives it undue weight. System 2 Attention (S2A) addresses this by having the model regenerate the input context to filter out irrelevant parts before answering. Achieved 80.3% accuracy on factual QA tasks.

## Optimization Output Format

Every optimization produces five deliverables:

**1. Analysis.** What the current prompt does well, what it's missing, and what's causing failures.

**2. Technique Recommendations.** Specific methods from the taxonomy matched to this prompt's task type, with rationale for each.

**3. Optimized Prompt.** The restructured version with improvements applied. Uses XML tags for structure where appropriate (<context>, <instructions>, <examples>).

**4. Rationale.** Why each change was made, what research supports it, and what trade-offs were considered.

**5. Testing Plan.** How to validate that the optimized prompt performs better than the original. What to test, what failure modes to watch for, and how to measure improvement.

## Evaluation Checklist

Before finalizing any prompt:

- [ ] Task directive is clear and cannot be misinterpreted
- [ ] Role assignment (if used) adds genuine value
- [ ] Context is complete but not padded with irrelevant information
- [ ] Examples are high-quality, diverse, and consistently formatted
- [ ] Output format is explicitly specified
- [ ] Reasoning approach matches the task complexity
- [ ] Edge cases and constraints are addressed
- [ ] No ambiguous language
- [ ] Resilient to prompt injection if processing external content
- [ ] Tested against at least 3 diverse inputs before deployment

## References

- **["The Prompt Report: A Systematic Survey of Prompting Techniques"](https://arxiv.org/abs/2406.06608)** (Schulhoff et al., 2024, updated Feb 2025). 1,500+ papers, 58 techniques. Primary taxonomy source.
- **["A Systematic Survey of Prompt Engineering in Large Language Models"](https://arxiv.org/abs/2402.07927)** (Sahoo et al., 2024, updated March 2025). 41+ techniques by application domain. Source for Chain-of-Draft, GoT, ThoT, LoT, Code Prompting, S2A, ECHO.
- **"Who Validates the Validators?"**: Three Gulfs framework for understanding where LLM evaluation breaks down.
- **Anthropic Claude documentation**: Model-specific optimization patterns (explicit instructions, XML structuring, context-before-instruction ordering).
- **Hamel Husain + Shreya Shankar**: Practical eval pipeline design for production AI systems.
- **Aakash Gupta**: AI PM evaluation methodology (AMI Cycle: Analyze, Measure, Improve).
- **Eugene Yan ("Abstractive")**: Reference-based vs. reference-free evaluation metrics for LLM outputs.

Built by Angel Torres | Alinea Consulting
Portfolio: https://axiomatic-second-9fc.notion.site/AI-Product-Management-Portfolio-312817fd0f37809bbe05e51aba6a6fd9
