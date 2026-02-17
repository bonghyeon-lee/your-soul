---
description: Update the 'Your Soul' profile based on recent user activity.
---

# Update 'Your Soul' Workflow

This workflow allows the agent to analyze recent user activity and update the `your-soul.md` file with new insights.

## Steps

1.  **Context Retrieval**:
    - Read `soul.config.json` to determine the output `language` (e.g., "ko" or "en") and enabled `metrics`.
    - Read the current content of `your-soul.md` to understand the current profile.
    - Read `docs/04-prompt.md` to understand the analysis criteria.
    - Gather recent user interactions (e.g., from `git log` or recent file modifications) or simply ask the user for the text/code they want to analyze. *For this initial phase, we will assume the agent has the context from the current conversation or a specific file provided by the user.*

2.  **Analysis**:
    - Analyze the provided context using the system prompt key points from `docs/04-prompt.md`.
    - **Language**: Ensure the analysis and output generation are in the language specified in `soul.config.json` (Default: "ko").
    - Identify:
        - Sentiment Trajectory
        - Cognitive Patterns (Blind Spots)
        - Soul DNA (Creativity, Logic, Empathy, Grit)
        - **Social Psychology Metrics** (Only analyze those enabled in `soul.config.json`):
            - Analyze Locus of Control, Regulatory Focus, etc. if enabled.
            - Assign confidence scores (0-100) based on evidence.
            - **Ignore** (set val: "N/A", conf: 0) if evidence is insufficient or the metric is disabled.

3.  **Draft Update**:
    - **For `your-soul.md`**: Update "Soul DNA" scores, "Social Psychology" confidence/values, and "Core Identity".
    - **For `logs/journal.md`**: Create a new narrative log entry (reverse chronology).

4.  **File Update**:
    - Update `your-soul.md` metrics using `multi_replace_file_content` or `replace_file_content`.
    - Append the new log entry to `logs/journal.md`. **Important**: Insert at the top of the log list (after the header) to maintain reverse chronological order.

## Example Trigger

"@antigravity update my soul based on the last refactoring task."
