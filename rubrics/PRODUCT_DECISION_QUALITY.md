# Product Decision Quality Rubric

Use this rubric to evaluate product decision quality under uncertainty. Score each dimension from 1 to 5, but do not let a total score hide a critical failure in framing, evidence integrity, diagnosis, or prioritization.

| Dimension | 1 — Weak | 3 — Sound | 5 — Excellent |
|---|---|---|---|
| Framing | Wrong decision or vanity outcome. | Generally right but broad or proxy-heavy. | Exact decision, outcome, user, scope, denominator, and constraints. |
| Analysis | Surface reading or calculation errors. | Core analysis is correct but limited. | Reproducible calculations, baselines, segments, contradictions, and mix shifts. |
| Evidence discipline | Assumptions or inferences presented as facts. | Mostly disciplined with minor overstatement. | Every material claim is labeled, traceable, and calibrated. |
| Diagnosis | Jumps from a datapoint to a solution. | Plausible diagnosis with limited alternatives. | Competing hypotheses, disconfirming evidence, confidence, prediction, and falsifier. |
| Solution quality | Cosmetic ideas or wrong altitude. | Relevant approaches with some overlap. | Small set of distinct, diagnosis-linked approaches with clear theories of change. |
| Prioritization | Arbitrary scoring or no real choice. | Reasonable but generic comparison. | Decision-specific criteria, no fake precision, clear first bet and sensitivity. |
| Strongest alternative | Missing or a strawman. | Credible but underdeveloped. | Fully steelmanned; its advantage and opportunity cost are explicit. |
| Trade-off | Generic pros and cons. | A trade-off is named. | A valuable benefit is consciously sacrificed for a more decisive advantage. |
| Execution | Feature list unrelated to the decision. | Plausible plan but broad. | Concrete mechanism, right-sized MVP, and coherent NOW/NEXT/NOT DOING. |
| Technology judgment | Technology used as a label. | Plausible but generic role. | Input/task/output, comparative advantage, failure modes, and guardrails are explicit; technology is omitted when unnecessary. |
| Metrics and validation | Vanity metrics or passive monitoring. | Reasonable metrics with weak actions. | Outcome, leading signal, diagnostics, guardrails, and actionable decision rules. |
| Reconsideration | “Iterate if it fails.” | Has reversal logic but levels blur. | Different triggers and actions for implementation, solution, and diagnosis failure. |
| Assumptions and uncertainty | Hidden assumptions drive the answer. | Visible but not prioritized. | Highest-leverage assumptions, contradictions, and residual risks are explicit. |
| Communication | Chronological analysis dump. | Clear but framework-shaped. | Recommendation-first story with nearby evidence, alternative, trade-off, plan, and defense. |
| Organizational usability | Ownership and decisions are unclear. | Owners and next steps mostly clear. | Decision owner, stakeholder roles, operating constraints, actions, and follow-up rules are unambiguous. |

## Interpretation

- **64–75:** exceptional decision quality;
- **52–63:** strong and ready with targeted refinement;
- **40–51:** plausible but material gaps remain;
- **below 40:** decision chain requires substantial rework.

## Critical-failure override

Regardless of total score, do not proceed when any of these is true:

- the work answers a different question than the brief;
- a material claim relies on fabricated or mislabeled evidence;
- the diagnosis does not follow from the evidence;
- the chosen approach does not address the diagnosis;
- dependencies or canonical versions cannot be verified.

## Reviewer prompts

Ask:

- What would a thoughtful dissenter say?
- Which assumption has the most leverage over the choice?
- Could the main metric improve while users or the business are worse off?
- What does the runner-up do better?
- What evidence would make us change course?
- Is the decision reversible, and is the process proportionate to its cost?
