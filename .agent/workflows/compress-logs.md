---
description: Compress and archive the 'Your Soul' journal logs.
---

# Compress Logs Workflow

This workflow summarizes the detailed entries in `logs/journal.md` and moves them to an archive, keeping the active journal clean.

## Steps

1.  **Read Journal**:
    - Read `logs/journal.md`.
    - If the file is small (e.g., < 5 entries), you might advise the user to wait.

2.  **Summarize**:
    - Analyze the entries to find key themes, shifts in personality, or major milestones.
    - Create a concise summary block (e.g., "Feb 2026 Summary: Focus on architecture and safety...").

3.  **Archive**:
    - Create a new archive file: `logs/archive/[YYYY-MM-DD]_journal_archive.md`.
    - Move the *entire current content* of `logs/journal.md` to this archive file.

4.  **Update Active Journal**:
    - Clear `logs/journal.md`.
    - Re-initialize it with the standard header.
    - (Optional) Add the summary note as the first entry to provide context.

5.  **Update Soul History**:
    - Append the summary to the "Recent Milestones" section in `your-soul.md` to keep a high-level history.

## Example Trigger

"@antigravity compress my logs"
