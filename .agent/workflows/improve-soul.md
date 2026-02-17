---
description: Analyze 'Your Soul' to suggest personal and system improvements.
---

# Improve 'Your Soul' Workflow

This workflow triggers a deep analysis of the current `your-soul.md` profile and the `update-soul.md` process to generate actionable advice for the user's personal growth and the system's accuracy.

## Steps

1.  **Context Retrieval**:
    -   Read `your-soul.md` to get the current "Soul DNA", "Blind Spots", and "Social Psychology" metrics.
    -   Read `soul.config.json` (if available) to see which metrics are enabled/disabled.
    -   Read `.agent/workflows/update-soul.md` to understand the available update mechanisms.

2.  **Gap Analysis**:
    -   **Persona Alignment**: Compare "Soul DNA" scores against the "Target Persona" description. (e.g., Does "Thoughtful Architect" align with low Creativity?)
    -   **Completeness Check**: Identify "Social Psychology" metrics that are marked as "N/A" or have low confidence scores (< 50%).
    -   **Blind Spot Check**: Review the "Blind Spots" section. Are there recurring patterns that need attention?

3.  **Strategy Generation**:
    -   **Personal Growth**: Suggest specific, small real-world actions to balance the Soul DNA.
        -   *Example*: If 'Empathy' is low, suggest: "Engage in a conversation where you only listen and ask questions for 10 minutes."
    -   **System Growth**: Suggest specific inputs to improve Profile Completeness.
        -   *Example*: If 'Openness to Experience' is "N/A", suggest: "Share a journal entry about a recent time you tried something new."
    -   **Process Optimization**: If the `update-soul.md` workflow hasn't been used recently (check `last_updated`), suggest running it with specific recent work contexts.

4.  **Output**:
    -   Generate a "Soul Improvement Report" (can be a temporary artifact or appended to a `growth_plan.md` if it exists).
    -   Format:
        -   **Reflect**: Brief summary of current state.
        -   **Act (Personal)**: 3 concrete actions for the user.
        -   **Feed (System)**: 3 concrete data inputs for the agent.

## Example Trigger

"@antigravity help me improve my soul"
or
"@antigravity what am I missing in my profile?"
