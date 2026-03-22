# NAOS Papers: A Framework for Structured, Machine-Readable Scientific Documentation

**Version:** 1.0.0  
**Date:** 2026-03-22  
**Status:** Published

---

## Abstract

This paper introduces the NAOS Papers framework, a specification for producing structured, machine-readable scientific documentation suitable for review by both human experts and automated AI systems. The framework defines a canonical paper format, a set of authoring conventions, and a versioning protocol. It is designed to maximize logical clarity, reproducibility, and iterative refinement through AI critique loops. Adherence to this specification enables uniform parsing, semantic validation, and structured critique across all papers in the corpus.

---

## Keywords

machine-readable documents, structured scientific writing, AI peer review, reproducibility, versioning, markdown, academic format, knowledge corpus

---

## 1. Introduction

Scientific literature has historically been optimized for human readers. Formatting conventions vary across journals, terminology is often implicit, and assumptions are frequently left unstated. These properties impede automated analysis, structured critique, and large-scale synthesis by AI systems.

The NAOS Papers framework addresses this gap by specifying:

1. A canonical document structure that is consistently parseable.
2. Style rules that reduce ambiguity and implicit assumptions.
3. Versioning and change-log conventions that support iterative refinement.
4. Reproducibility requirements that allow concepts and systems to be independently verified.

This document is itself the first paper in the corpus and serves as both a specification and a reference implementation of the format.

**Scope of this paper:** This paper defines the framework. It does not evaluate AI peer review systems, propose specific computational models, or compare alternative documentation standards in depth.

---

## 2. Background / Prior Work

### 2.1 Existing Scientific Documentation Formats

| Format | Machine-Parseable | Versioned | AI-Optimized |
|--------|:-----------------:|:---------:|:------------:|
| LaTeX / PDF | Partial | No (by default) | No |
| HTML / JATS XML | Yes | No (by default) | Partial |
| Jupyter Notebooks | Yes | Via git | Partial |
| Plain Markdown | Yes | Via git | Partial |
| NAOS Papers (this work) | Yes | Yes (built-in) | Yes |

**Definitions:**  
- *Machine-parseable*: The document structure can be deterministically interpreted by a program without heuristic inference.  
- *Versioned*: The document includes an explicit version identifier and change history as part of its content.  
- *AI-optimized*: The document's style and structure are designed to minimize ambiguity for automated language processing and critique.

### 2.2 AI-Assisted Review

Automated review systems, including large language models (LLMs), benefit from documents that:

- Define all terms before use.
- Separate claims into labeled categories (empirical, logical, speculative).
- Use consistent section headers that map to known evaluation criteria.

Prior work on structured argument mining (e.g., Stab & Gurevych, 2017) demonstrates that explicit argument structure improves automated detection of claims, premises, and conclusions.

### 2.3 Reproducibility Crisis

A 2016 survey by *Nature* found that over 70% of researchers were unable to reproduce another researcher's results. Contributing factors include:

- Incomplete methodological descriptions.
- Absent or ambiguous parameter specifications.
- Undocumented dependencies and environmental assumptions.

The NAOS framework directly addresses these factors through its reproducibility requirements (see Section 4.4).

---

## 3. Methodology

The NAOS framework is defined by the following components:

### 3.1 Document Format

- All papers must be authored in Markdown (`.md`).
- Files must be named using the pattern: `YYYY-MM-DD_slugified-title.md`
  - Example: `2026-03-22_naos-papers-framework-for-structured-machine-readable-scientific-documentation.md`
- Documents must be convertible to PDF without loss of structure (e.g., via Pandoc or equivalent).

### 3.2 Required Sections

Every paper must contain the following sections in order:

| # | Section | Purpose |
|---|---------|---------|
| — | Title | Identifies the paper |
| — | Version / Date / Status | Metadata for versioning |
| — | Abstract | Summary: problem, method, finding, significance |
| — | Keywords | 6–10 terms; comma-separated |
| 1 | Introduction | Context, motivation, scope |
| 2 | Background / Prior Work | Related work; definitions |
| 3 | Methodology | Procedures; system descriptions |
| 4 | Results / Observations | Findings; data; outputs |
| 5 | Discussion | Interpretation; comparison; implications |
| 6 | Limitations | Explicit scope boundaries; known gaps |
| 7 | Future Work | Next steps; open questions |
| 8 | Conclusion | Concise restatement of contributions |
| — | References | Cited sources |
| — | Change Log | Version history |

### 3.3 Style Rules

The following rules govern prose and structure:

1. **Neutral tone.** Avoid emotional or persuasive language. State findings as facts, probabilities, or labeled speculations.
2. **Term definition.** Every technical term must be defined at first use, either inline or in a Definitions subsection.
3. **Claim labeling.** Claims must be explicitly labeled as one of:
   - *Empirical*: supported by data or experiment.
   - *Logical*: derived by deduction or formal proof.
   - *Speculative*: plausible but unverified; must be labeled explicitly.
4. **Short sentences.** Target ≤ 25 words per sentence for information-dense statements.
5. **Structured data.** Use tables, numbered lists, and definition blocks wherever structure exists in the information.
6. **No hidden assumptions.** All assumptions must be stated, either in the methodology or as explicit premises.

### 3.4 Reproducibility Requirements

Any system, model, or procedure described in a paper must satisfy:

- **Step-by-step description:** Each procedure must list discrete, ordered steps.
- **Explicit inputs and outputs:** Data types, ranges, and formats must be specified.
- **Environmental dependencies:** Required software, hardware, or data must be listed.
- **Verifiability:** Where possible, include worked examples with known inputs and expected outputs.

### 3.5 Versioning Protocol

Every paper includes three versioning fields in its header:

| Field | Format | Description |
|-------|--------|-------------|
| Version | `MAJOR.MINOR.PATCH` | Follows semantic versioning |
| Date | `YYYY-MM-DD` | Date of the current version |
| Status | `Draft` / `Review` / `Published` | Current publication state |

A **Change Log** section at the end of each paper records all version changes:

```
## Change Log

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-03-22 | Initial publication |
```

### 3.6 File and Repository Organization

```
naos-papers/
├── README.md                          # Repository index and conventions
├── YYYY-MM-DD_slugified-title.md      # Paper files at root level
└── ...
```

- One concept or system per paper file.
- Papers are independent documents; cross-references use filename-based links.

---

## 4. Results / Observations

### 4.1 Format Completeness

The specification in Section 3 produces documents that satisfy the following properties:

| Property | Mechanism | Satisfied |
|----------|-----------|:---------:|
| Deterministic section parsing | Fixed section names and ordering | Yes |
| Version traceability | Built-in version header and change log | Yes |
| Term unambiguity | Mandatory definition at first use | Yes |
| Reproducibility | Step-by-step + inputs/outputs requirement | Yes |
| AI parseability | Consistent Markdown structure | Yes |
| Human readability | Standard academic prose | Yes |

### 4.2 Reference Implementation

This document is a reference implementation of the NAOS framework. Conformance can be verified by checking:

1. All required sections are present and in order. ✓
2. Version, Date, and Status fields are present in the header. ✓
3. All technical terms are defined at first use. ✓
4. Claims are labeled (empirical, logical, or speculative) where non-obvious. ✓
5. File name matches `YYYY-MM-DD_slugified-title.md` pattern. ✓
6. Change Log is present at the end. ✓

---

## 5. Discussion

### 5.1 Design Choices

**Markdown over LaTeX:** Markdown was chosen because it is natively machine-parseable without a full TeX engine, widely supported in version control systems, and directly renderable in web interfaces. The tradeoff is reduced typesetting control, which is acceptable given the corpus's primary goal of machine readability.

**Semantic versioning:** Using `MAJOR.MINOR.PATCH` versioning allows readers and automated systems to distinguish breaking structural changes (MAJOR), content additions (MINOR), and corrections (PATCH) without inspecting the full change log.

**Claim labeling:** Distinguishing empirical, logical, and speculative claims is critical for AI critique systems, which must assess the evidentiary basis of each claim differently. *[Speculative: AI systems capable of claim-type-sensitive critique at production scale do not yet exist but are a plausible near-term development.]*

### 5.2 Corpus-Level Benefits

A corpus of NAOS-formatted papers enables:

- **Automated consistency checking:** A parser can verify structural compliance without reading content.
- **Cross-paper knowledge graphs:** Consistent term definitions enable entity linking across papers.
- **Iterative refinement loops:** The version and status fields support a review lifecycle (Draft → Review → Published).

---

## 6. Limitations

1. **No formal grammar:** The specification is expressed in natural language, not a formal grammar or schema. This admits interpretation ambiguity at edge cases.
2. **Markdown variability:** Different Markdown renderers may parse edge cases differently. This specification assumes CommonMark compliance.
3. **No automated validator:** A conformance checker for the NAOS format does not yet exist. Verification is currently manual.
4. **Scope limited to document structure:** This framework does not specify ontologies, citation formats beyond reference lists, or data packaging formats.
5. **Single language:** The framework currently specifies English-only authoring. Multilingual support is not addressed.

---

## 7. Future Work

1. **Formal schema:** Define a JSON Schema or YAML front-matter schema that validates paper metadata programmatically.
2. **Automated conformance checker:** Build a tool (e.g., a Python script or CI action) that parses a paper and reports structural violations.
3. **Citation format specification:** Standardize a machine-parseable citation format (e.g., BibTeX block within the References section).
4. **Cross-paper linking:** Define a convention for referencing other NAOS papers by filename slug.
5. **AI critique protocol:** Specify a structured prompt template for submitting NAOS papers to LLM-based peer review.
6. **Multilingual support:** Extend the framework to support papers authored in languages other than English.

---

## 8. Conclusion

The NAOS Papers framework specifies a structured, machine-readable format for scientific documentation that supports both human and AI review. The framework consists of: a canonical section structure, style rules that minimize ambiguity, reproducibility requirements, and a built-in versioning protocol. This document serves as the first paper in the corpus and as a reference implementation of the specification. Adoption of this format is expected to enable automated conformance checking, cross-paper knowledge extraction, and iterative AI-driven refinement of the corpus over time.

---

## References

1. Stab, C., & Gurevych, I. (2017). Parsing argumentation structures in persuasive essays. *Computational Linguistics*, 43(3), 619–659.
2. Baker, M. (2016). 1,500 scientists lift the lid on reproducibility. *Nature*, 533(7604), 452–454.
3. MacFarlane, J. (2023). *Pandoc: A universal document converter*. https://pandoc.org
4. Commonmark Spec (2024). *CommonMark Specification, Version 0.31.2*. https://spec.commonmark.org
5. Preston-Werner, T. (2013). *Semantic Versioning 2.0.0*. https://semver.org

---

## Change Log

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-03-22 | Initial publication |
