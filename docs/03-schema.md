# 03. Schema: Your Soul Data Structure

This document defines the schema for the `your-soul.md` file, which serves as the "Digital Soul" of the user.

## File Format

The file is a valid Markdown file with a YAML frontmatter for machine-readable metadata, followed by human-readable sections.

## 1. YAML Frontmatter (Machine Readable)

```yaml
---
last_updated: "2026-02-08T12:00:00Z"
version: "1.0.0"
soul_dna:
  creativity: 85
  logic: 72
  empathy: 60
  action: 90
target_persona: "Empathetic Leader"
current_alignment_score: 65
blind_spots:
  - "Overuse of 'Actually'"
  - "Dismissive of emotional context"
social_psychology:
  profile_completeness: 0
  locus_of_control: { value: "N/A", confidence: 0, evidence: "" }
  regulatory_focus: { value: "N/A", confidence: 0, evidence: "" }
  openness_to_experience: { value: "N/A", confidence: 0, evidence: "" }
  self_monitoring: { value: "N/A", confidence: 0, evidence: "" }
  attachment_style: { value: "N/A", confidence: 0, evidence: "" }
  defense_mechanisms: { value: "N/A", confidence: 0, evidence: "" }
---
```

## 2. Human-Readable Content (Markdown)

### Header

```markdown
# [Your Name]'s Soul
> "A mirror that reflects the unseen."
```

### Section 1: Core Identity (The Essence)

* **Keywords**: List of 3-5 keywords that define the user's current state.
* **One-Liner**: A single sentence summarizing the user's persona.
* **Soul DNA Visualization**: (ASCII Art or Link to generated image) representing the `soul_dna` metrics.

### Section 2: Communication Pattern (The Voice)

* **Tone**: e.g., Direct, Sarcastic, Polite, Hesitant.
* **Vocabulary Habits**: Frequently used words or phrases.
* **Blind Spots**:
  * *Warning*: "You tend to apologize unnecessarily."
  * *Observation*: "You avoid answering personal questions."

### Section 3: Intellectual & Work Style (The Mind)

* **Problem Solving**: Top-down vs Bottom-up? Intuitive vs Analytical?
* **Interests**: precise topics the user is currently obsessed with.
* **Strengths**: What the user does best (e.g., "Debugging complex logic", "Explaining concepts simply").

### Section 4: Social Psychology (The Deep Dive)

* **Profile Completeness**: [====------] 40% (Based on high-confidence metrics)

* **Locus of Control**: *Internal* (Confidence: 80%)
  > Evidence: "I can fix this."
* **Regulatory Focus**: *Promotion* (Confidence: 60%)
  > Evidence: "Let's try a new approach."
* ... (Other metrics follow similar pattern)

### Section 4: Growth Log (The Journey)

A reverse-chronological log of "Soul Diffs".

#### [YYYY-MM-DD]

* **Focus**: What was the main theme of today's interactions?
* **Alignment**: 65% -> 68% match with "Empathetic Leader" persona.
* **Key Feedback**: "Today you listened more than you spoke. Good job on asking 'Why' before offering a solution."
* **Action Item**: "Try to acknowledge the emotion before fixing the bug in the next conversation."

---

## 3. JSON Schema Representation (For Validation)

```json
{
  "type": "object",
  "properties": {
    "metadata": {
      "type": "object",
      "properties": {
        "last_updated": { "type": "string", "format": "date-time" },
        "soul_dna": {
          "type": "object",
          "properties": {
            "creativity": { "type": "integer", "min": 0, "max": 100 },
            "logic": { "type": "integer", "min": 0, "max": 100 },
            "empathy": { "type": "integer", "min": 0, "max": 100 },
            "action": { "type": "integer", "min": 0, "max": 100 }
          }
        },
        "social_psychology": {
          "type": "object",
          "properties": {
            "profile_completeness": { "type": "integer", "min": 0, "max": 100 },
            "locus_of_control": { "$ref": "#/definitions/metric" },
            "regulatory_focus": { "$ref": "#/definitions/metric" },
            "openness_to_experience": { "$ref": "#/definitions/metric" },
            "self_monitoring": { "$ref": "#/definitions/metric" },
            "attachment_style": { "$ref": "#/definitions/metric" },
            "defense_mechanisms": { "$ref": "#/definitions/metric" }
          }
        }
      }
    },
    "content": {
      "type": "object",
      "properties": {
        "core_identity": { ... },
        "communication": { ... },
        "social_psychology": { ... },
        "growth_log": { "type": "array", "items": { ... } }
      }
    }
  },
  "definitions": {
    "metric": {
      "type": "object",
      "properties": {
        "value": { "type": "string" },
        "confidence": { "type": "integer", "min": 0, "max": 100 },
        "evidence": { "type": "string" }
      }
    }
  }
  }
}
```
