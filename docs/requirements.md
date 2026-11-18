# PropertyIQ — Business Requirements

**Status:** Initial business requirements, subject to design and refinement.

## 1. Use case

A property management company manages approximately 150 residential and commercial properties. Documents such as tenancy agreements, maintenance contracts, building policies, inspection reports, and tenant handbooks are stored across locations and versions.

Staff often search and compare these documents manually when answering tenant questions, checking repair responsibilities, or determining which policy applies.

**Goal:** Provide an internal AI-assisted document search and question-answering application that returns accurate, evidence-backed answers, preserves source traceability, respects access rights, and highlights conflicts or gaps in the underlying records.

## 2. Users

- **Property manager:** Asks questions and reviews referenced evidence for assigned properties.
- **Administrator:** Manages documents, versions, and property access.
- **Business reviewer (initially an administrator):** Reviews answer quality and reliability using evaluation reports.

## 3. Business requirements

| ID | Requirement |
| --- | --- |
| BR-01 | Users must be able to upload and manage property documents in PDF and DOCX formats. |
| BR-02 | Users must be able to ask natural-language questions about properties, agreements, and policies. |
| BR-03 | The system must provide answers grounded in the uploaded documents. |
| BR-04 | Every factual answer must include source document references and page numbers where available. |
| BR-05 | Users must be able to ask questions that require information from multiple documents. |
| BR-06 | The system must identify conflicting information across documents and clearly communicate discrepancies. |
| BR-07 | The system must distinguish current documents from outdated or superseded versions. |
| BR-08 | The system must indicate when sufficient information is unavailable rather than invent an answer. |
| BR-09 | Users must only be able to access documents belonging to properties they are authorised to manage. |
| BR-10 | Administrators must be able to add, update, replace, and delete documents. |
| BR-11 | Users must be able to view the supporting document passages behind an answer. |
| BR-12 | The business must be able to evaluate answer accuracy, source reliability, and response times. |

## 4. Example scenario

**Question:** "Who is responsible for repairing the leaking pipe in Apartment 204, and what is the required response time?"

**Expected outcome:**
1. Determine which property and tenancy record the question concerns.
2. Consult the applicable tenancy agreement and current maintenance policy.
3. State the repair responsibility and response time only if supported by those documents.
4. Show the document name, page (when available), and relevant supporting passage for each material claim.
5. If documents conflict or information is missing, describe the uncertainty rather than selecting a fact without support.
6. Do not use documents the signed-in user is not authorised to access.

## 5. Business acceptance criteria

- **Document management (BR-01, BR-10):** An administrator can add a PDF or DOCX document, update or replace it, and delete it. Document status and version are visible.
- **Answer provenance (BR-02, BR-03, BR-04, BR-11):** A supported answer includes a source reference that opens the associated document passage and page when a page exists.
- **Multi-document questions (BR-05):** The system can answer a question that requires evidence from at least two authorised documents, with a reference to each.
- **Conflicts and versioning (BR-06, BR-07):** Conflicting clauses and superseded versions are surfaced clearly; outdated material is not silently presented as current policy.
- **No-evidence behaviour (BR-08):** For a question lacking sufficient evidence, the system responds that it cannot verify the answer from available documents.
- **Access control (BR-09):** A user with access to Property A but not Property B cannot retrieve, view, or receive information sourced solely from Property B documents.
- **Quality reporting (BR-12):** Reviewers can run a known question set and inspect answer correctness, source-reference quality, and response-time measurements.

## 6. Initial scope boundaries

- Staff-only application. No tenant-facing portal in the first release.
- No automated maintenance work orders or supplier actions in the first release.
- The application assists staff with locating evidence; it does not issue legal determinations.
- Demonstration content will be fictional or explicitly licensed for redistribution.

## 7. Open design questions

- What property, document, user, and permission identifiers should be used?
- How should a document be designated current or superseded?
- How should conflicting source clauses be presented and reviewed?
- What benchmarks and minimum quality thresholds constitute acceptance?
- What should happen when a PDF lacks reliable page-level extraction?

These questions are intentionally left open for the technical architecture phase.
