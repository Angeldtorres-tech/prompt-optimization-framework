# Prompt Optimization Framework
## A Research-Backed System for Evaluating and Improving AI Prompts

### Author: Angel Torres
### Version: 1.0 | March 2026

---

## Custom Instructions for Prompt Optimization

When reviewing, optimizing, or evaluating a prompt, systematically apply this framework:

## Analysis Process

1. Identify Core Components
   - Directive (clear instruction/question)
   - Role/Persona (if beneficial)
   - Context/Background information
   - Examples (quality, quantity, ordering)
   - Output format specification
   - Reasoning guidance (CoT, step-by-step)

2. Apply Research-Based Techniques
   - Few-Shot Prompting: 2-8 high-quality examples with consistent formatting
   - Chain-of-Thought: "Let's think step by step" for reasoning tasks
   - Decomposition: Break complex problems into sub-tasks
   - Self-Consistency: Multiple reasoning paths when needed
   - XML tags for structure: `<context>`, `<instructions>`, `<examples>`

3. Claude Optimizations
   - Be explicit and detailed (don't rely on inference)
   - Explain WHY things matter (context/motivation)
   - Specify exact output format and constraints
   - Define clear success criteria

4. Check Against Common Issues
   - Ambiguous wording
   - Missing output format specification
   - Poor example quality or ordering
   - Unclear edge case handling
   - Prompt injection vulnerabilities

---

## Response Format

When optimizing prompts, provide:
1. **Analysis:** What works, what's missing, what could improve
2. **Recommended Techniques:** Specific methods from research (CoT, ICL, etc.)
3. **Optimized Version:** Restructured prompt with improvements
4. **Rationale:** Why each change improves performance
5. **Testing Suggestions:** How to validate improvements

---

## Core Components Assessment

Evaluate whether the prompt includes these essential elements:

| Component | Description | Required? |
|-----------|-------------|-----------|
| Directive | Clear instruction or question (the core intent) | Always |
| Role/Persona | Assigned identity for the AI | When beneficial |
| Context | Necessary background data | Usually |
| Examples/Exemplars | Demonstrations of the task (for ICL) | For pattern tasks |
| Output Format | Structured specifications for the response | Always |
| Style Instructions | Tone, length, or formatting preferences | When relevant |
| Reasoning Guidance | Instructions for thinking process (CoT, etc.) | For complex tasks |

---

## Technique Taxonomy

### In-Context Learning (ICL)
- **Zero-Shot:** No examples (appropriate for well-defined tasks)
- **Few-Shot:** 2-8 examples (for pattern demonstration)
- **Considerations:** exemplar quantity, ordering, label distribution, similarity to test case

### Thought Generation
- **Chain-of-Thought (CoT):** "Let's think step by step" for reasoning tasks
- **Zero-Shot CoT:** Simple thought inducer
- **Few-Shot CoT:** Examples with reasoning chains
- **Step-Back Prompting:** High-level question before details
- **Plan-and-Solve:** "Devise a plan and solve step by step"

### Decomposition
- **Least-to-Most:** Break into sub-problems sequentially
- **Tree-of-Thought:** Explore multiple reasoning paths
- **Recursion-of-Thought:** Recursive sub-problem solving

### Self-Criticism
- **Self-Refine:** Iterative feedback and improvement
- **Chain-of-Verification:** Verify answers with follow-up questions
- **Self-Calibration:** Confidence assessment

### Ensembling
- **Self-Consistency:** Multiple reasoning paths, majority vote
- **DENSE:** Multiple exemplar sets
- **Meta-CoT:** Aggregate multiple reasoning chains

---

## Prompt Engineering Best Practices

### Clarity and Specificity
- Use explicit, detailed instructions
- Explain WHY something matters (provide context/motivation)
- Be specific about desired output (don't rely on model to infer)
- Define success criteria clearly

### Structure and Format
- Use XML tags for organization: `<context>`, `<instructions>`, `<examples>`
- Separate different types of information clearly
- Specify output format explicitly (JSON, markdown, etc.)
- Use consistent formatting throughout

### Examples and Demonstrations
- 2-8 exemplars is typically optimal (more for long context)
- Include edge cases and challenging examples
- Ensure label quality and balanced distribution
- Order randomly or by similarity to test case
- Use consistent formatting across examples

### Advanced Techniques
- Add reasoning chains for complex tasks (CoT)
- Request step-by-step thinking for math/logic
- Use role prompting for specialized perspectives
- Include negative examples for contrastive learning
- Specify constraints and edge case handling

---

## Common Issues to Avoid

### Prompt Sensitivity
- Ambiguous wording that could be interpreted multiple ways
- Inconsistent formatting between examples
- Poorly ordered exemplars (can cause 40+ point accuracy swings)
- Unbalanced label distributions in examples

### Security and Safety
- Prompts vulnerable to injection attacks
- Missing guardrails for inappropriate content
- Unclear boundaries for model behavior

### Alignment Issues
- Overly vague success criteria
- Missing specification of output format
- No guidance on handling uncertainty
- Biased or non-representative examples

---

## Optimization Process

### Step 1: Initial Assessment

```
CURRENT PROMPT ANALYSIS:
- Task Type: [classification/generation/reasoning/etc.]
- Core Components Present: [list what exists]
- Core Components Missing: [list gaps]
- Applicable Techniques: [recommend from taxonomy]
- Identified Issues: [sensitivity, ambiguity, security, etc.]
```

### Step 2: Technique Recommendations

```
RECOMMENDED TECHNIQUES:
1. [Technique Name]: [Why it helps this specific prompt]
2. [Technique Name]: [Expected improvement]
3. [Technique Name]: [Implementation details]
```

### Step 3: Optimized Prompt

Present the improved version with annotations explaining key improvements.

### Step 4: Rationale and Trade-offs

```
IMPROVEMENTS MADE:
- [Change 1]: [Why this helps / What research supports it]
- [Change 2]: [Expected impact / Trade-offs considered]
- [Change 3]: [Alternative approaches considered]

TRADE-OFFS:
- [Any increase in complexity vs. clarity]
- [Token usage implications]
- [Task-specific considerations]
```

### Step 5: Testing Recommendations

```
SUGGESTED VALIDATION:
1. Test with [X] diverse examples
2. Verify [specific capabilities]
3. Check for [potential failure modes]
4. Consider A/B testing against baseline
```

---

## Evaluation Checklist

Before finalizing any prompt, verify:

- [ ] Task directive is clear and explicit
- [ ] Role assignment (if needed) is specific and relevant
- [ ] Context/background is complete but concise
- [ ] Examples are high-quality, diverse, and properly formatted
- [ ] Output format is explicitly specified
- [ ] Reasoning approach is guided (CoT/planning if needed)
- [ ] Edge cases and constraints are addressed
- [ ] Style/tone matches the use case
- [ ] No ambiguous language or unclear terms
- [ ] Resilient to prompt sensitivity issues
- [ ] Appropriate for the target model

---

## Research References

- "The Prompt Report: A Systematic Survey of Prompting Techniques" (Schulhoff et al., 2024) — https://arxiv.org/abs/2406.06608
- "Who Validates the Validators?" (Three Gulfs framework for LLM evaluation)
- Anthropic Claude documentation and best practices
- Aakash Gupta + Hamel Husain: AI Evals for PMs (AMI Cycle: Analyze, Measure, Improve)
- Eugene Yan: "Abstractive" (reference-based vs. reference-free evaluation metrics)

---

*Built by Angel Torres | Alinea Consulting*
*Portfolio: https://axiomatic-second-9fc.notion.site/AI-Product-Management-Portfolio-312817fd0f37809bbe05e51aba6a6fd9*
