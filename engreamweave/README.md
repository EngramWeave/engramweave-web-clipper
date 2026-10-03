# EngramWeave - Web Clipper Resources

This directory contains EngramWeave-specific resources and templates for the [Obsidian Web Clipper](https://github.com/obsidianmd/obsidian-clipper) fork.

Currently, EngramWeave relies entirely on the upstream official template system without requiring modifications to the core extension codebase.

---

## 🚀 How to Use

1. Open **Obsidian Web Clipper Settings**.
2. Navigate to the **Templates** tab.
3. Click **Import** and select [`EngramWeave-Web-source.json`](./EngramWeave-Web-source.json).
4. Set it as your default template (or use it when capturing web pages into your vault).

---

## 📑 Web Source Template

The **EngramWeave Web Source** template standardizes how web materials enter an EngramWeave vault:

- **Storage Location**: Saves content as readable Markdown under `20_Sources/Web/`.
- **Metadata Preservation**: Preserves original URL, title, and capture timestamp.
- **User Annotation**: Provides an editable `annotation` field for real-time capture notes.
- **Downstream Ready**: Generates records formatted for discovery and ingestion by EngramWeave Core.

---

## 🏷️ Raw Source Convention

Clipped web pages follow the EngramWeave raw-source convention with the following core frontmatter properties:

```yaml
---
type: raw_source
source_type: web
title: "{{title}}"
source: "{{url}}"
captured_at: "{{date}}"
annotation: ""
---
```

*Optional fields such as `author`, `published_date`, `site_name`, and `tags` are included when available.*

### `annotation` Field Policy

The `annotation` property records the user's **original cognitive context** (`原始认知上下文`) authored at capture time. It captures spontaneous human intent rather than objective page text, including:

- **Capture Rationale**: Why this material was saved.
- **Key Takeaways & Highlights**: Core insights and standout excerpts.
- **Thoughts & Doubts**: Immediate impressions, critiques, or skepticism.
- **Questions & Next Steps**: Unresolved questions and future research directions.
- **Knowledge Synthesis**: Initial associations, connection ideas, or vault organization advice.

#### Processing Principles
- **High-Priority User Context**: Downstream AI pipelines must treat `annotation` as first-class, high-priority intent—never conflating it with ordinary web source content.
- **Integrity Guarantee**: Downstream processing must **never** silently overwrite, alter, or discard the original user annotation. It may be left empty.

---

## 💡 Design Principles

**Capture Only**: The Web Clipper is intentionally decoupled from backend logic.

- ❌ Does not connect directly to EngramWeave Core
- ❌ Does not trigger compilation, manage AI jobs, or maintain processing states
- ❌ Does not assign internal system IDs
- ✅ **EngramWeave Core** scans, discovers, and processes `raw_source` files asynchronously from the vault.

---

## 🔄 Upstream Maintenance

This project tracks the official Obsidian Web Clipper. For sync strategies and maintenance workflows, refer to [UPSTREAM.md](../UPSTREAM.md).