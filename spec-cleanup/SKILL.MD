---
name: spec-cleanup
description: Final-pass cleanup of specs/design docs to remove iteration
  artifacts. Use when finalizing a document that went through multiple
  drafts, or when asked to "clean up", "finalize", or "publish" a spec.
---

# Spec Cleanup

Rewrite the document as a standalone specification. The reader has never
seen any previous version. 

## Constraints
- **Preserve Structure:** Do not restructure the document, change heading levels, or merge sections unless absolutely necessary. Keep the original hierarchy.
- **Dry & Technical Tone:** Use direct, authoritative language. No conversational filler, no meta-commentary ("This section details...", "As shown below...").
- **No Hallucinations:** Do not invent new features, requirements, or technical details to fill gaps. If a section is empty after cleanup, delete it or flag it.

## Remove
- **Historical Baggage:** References to prior drafts, versions, or rejected alternatives ("previously", "instead of the old X", "unlike v1", "updated to", "(new)").
- **Phantom Comparisons:** Comparisons against designs that no longer exist in the doc.
- **Orphaned Sections:** Headings whose content was gutted by edits, or sections only meaningful relative to removed content.
- **Change Rationale:** Justifications framed as change rationale ("we switched to X because the old approach..."). Restate as direct design rationale or move to `DECISIONS.md`.
- **Stale Artifacts:** Outdated code snippets, deprecated config flags, or Mermaid/PlantUML diagrams that no longer match the current text.
- **Unresolved Placeholders:** `TODO`, `TBD`, `FIXME`, or `[Needs Review]` markers. (If you cannot resolve them, move them to a dedicated "Open Questions" section at the end).

## Verify
- **Necessity:** Every section is strictly necessary for the CURRENT design.
- **Cohesion:** No section references another section that no longer exists.
- **Terminology:** Terminology is consistent throughout (renames fully propagated).
- **Links:** All internal markdown links (`[text](#anchor)`) point to valid, existing headings.
- **Vibe Check:** The doc reads as if written in one sitting by a single author.

## Output
1. The cleaned, standalone spec in Markdown.
2. A brief `## Changelog & Relocations` section at the very bottom listing:
   - Sections/content that were deleted.
   - Content that was moved (e.g., "Moved old auth rationale to DECISIONS.md").
   - Unresolved TODOs that were flagged.