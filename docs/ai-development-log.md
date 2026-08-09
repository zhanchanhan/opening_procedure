# AI Development Log

This is a concise evidence log, not a transcript dump. It records the problem, how AI helped, the human decision, and the validation used to accept the result.

## 1. From operational notes to a usable workflow

**Problem**

Opening tasks mixed timing, location, safety notes, and responsibility. A flat list would be difficult to scan while moving through a store.

**AI contribution**

AI helped propose task grouping, concise labels, warning treatments, and a mobile interaction sequence.

**Human decision**

The final hierarchy follows how staff physically move through the workflow: arrival, preparation, front-of-house, environment, then final confirmation. Important constraints remain visible on the task card rather than hidden in a separate manual.

**Validation**

- Confirm every task belongs to exactly one section.
- Verify the total displayed count matches the data model.
- Complete the flow on a narrow mobile viewport.

## 2. Photo evidence without a backend

**Problem**

Phone photos can be several megabytes. Embedding multiple originals in browser state or a portable report quickly exceeds practical limits.

**AI contribution**

AI helped explore Canvas resizing, JPEG quality reduction, progressive compression, and size-budget strategies.

**Human decision**

The prototype first resizes images for preview, then applies a stricter per-photo budget when producing the report. This keeps the demo dependency-free and makes the constraint visible in code.

**Validation**

- Upload landscape and portrait photos.
- Confirm aspect ratios remain correct.
- Open the downloaded report offline.
- Test multiple photos and observe generation time on a phone.

## 3. Public-demo security redesign

**Problem**

The initial prototype placed an EmailJS recipient and client identifiers in public frontend code. Even when a provider calls a value a public key, an unrestricted public workflow can leak contact information and invite abuse.

**AI contribution**

AI-assisted review identified the difference between a working internal prototype and a safe public portfolio artifact, then generated alternative reporting flows.

**Human decision**

The portfolio version removes the external email SDK and all recipient/service configuration. It creates a self-contained HTML report with a Blob URL and downloads it locally. User-entered text is escaped before insertion into the report.

**Validation**

- Search the repository for the old provider and recipient identifiers.
- Generate a report while observing the browser Network panel.
- Enter HTML-like text in the name and notes fields and confirm it renders as text.
- Confirm the report includes a local-generation privacy notice.

## Working principle

> AI produces options and implementation candidates. The developer defines constraints, rejects unsafe shortcuts, and accepts a change only after inspecting and verifying its behavior.
