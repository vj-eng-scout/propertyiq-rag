Update the existing docs/design.md for the manager-only experiment. This is a design task, not an implementation task.

Acceptance criteria:

Show the shared components and data flow from fictional PDF/DOCX ingestion through PostgreSQL retrieval to a cited answer in Next.js.
Trace the Apartment 204 question through both strategies: one search for the baseline, and at most one optional targeted follow-up for agentic RAG. Show what happens if evidence remains missing or conflicts.
Mark where the server enforces property access, current-version filtering and citation validation, including access checks when opening a source.
Identify what stays fixed across both strategies and how answer quality, latency and cost will inform the architecture decision. Keep administrator workflows out of scope.