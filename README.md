# naos-papers

A collection of scientific-style papers intended for structured reasoning, clarity, and peer review by both humans and AI systems.

---

## Repository Structure

```
naos-papers/
├── README.md                          # This file — index and conventions
├── YYYY-MM-DD_slugified-title.md      # Paper files at root level
└── ...
```

Each paper is a self-contained Markdown file. One concept or system per file.

---

## Paper Format

Every paper follows this structure, in order:

| Section | Description |
|---------|-------------|
| Title | Identifies the paper |
| Version / Date / Status | Versioning metadata |
| Abstract | Summary: problem, method, finding, significance |
| Keywords | 6–10 comma-separated terms |
| 1. Introduction | Context, motivation, scope |
| 2. Background / Prior Work | Related work; term definitions |
| 3. Methodology | Procedures; system descriptions |
| 4. Results / Observations | Findings; data; outputs |
| 5. Discussion | Interpretation; comparison; implications |
| 6. Limitations | Explicit scope boundaries; known gaps |
| 7. Future Work | Next steps; open questions |
| 8. Conclusion | Concise restatement of contributions |
| References | Cited sources |
| Change Log | Version history |

---

## File Naming Convention

```
YYYY-MM-DD_slugified-title.md
```

Example: `2026-03-22_naos-papers-framework-for-structured-machine-readable-scientific-documentation.md`

---

## Style Rules

1. **Neutral tone** — no emotional or persuasive language.
2. **Define all terms** at first use.
3. **Label claims** as *Empirical*, *Logical*, or *Speculative*.
4. **Short sentences** — target ≤ 25 words for information-dense statements.
5. **Structured data** — use tables, numbered lists, and definition blocks wherever structure exists.
6. **No hidden assumptions** — state all assumptions explicitly.

---

## Versioning

Each paper header includes:

| Field | Format | Values |
|-------|--------|--------|
| Version | `MAJOR.MINOR.PATCH` | Semantic versioning |
| Date | `YYYY-MM-DD` | Date of current version |
| Status | string | `Draft`, `Review`, `Published` |

---

## Papers

| File | Title | Date | Version | Status |
|------|-------|------|---------|--------|
| [2026-03-22_naos-papers-framework-for-structured-machine-readable-scientific-documentation.md](./2026-03-22_naos-papers-framework-for-structured-machine-readable-scientific-documentation.md) | NAOS Papers: A Framework for Structured, Machine-Readable Scientific Documentation | 2026-03-22 | 1.0.0 | Published |
