# Engineering Documentation Governance

**Status:** `CANONICAL`  
**Audience:** Humans + AI Agents  
**Purpose:** Prevent documentation entropy, enforce clarity, and enable printable, signable design freezes.

---

## 1. Final Conclusion (Non-Negotiable)

The **Canonical System + Atomic Feature SDDs + Compiled Approval Artifact** model is the minimum structure required to prevent chaos.

- **Separation** is for authoring.
- **Compilation** is for approval and printing.
- **Stakeholders sign Compiled Artifacts (DFA)**, not working markdown files.

> [!IMPORTANT]
> **Blueprint ≠ Printed bundle**  
> **Printed bundle = Design Freeze Artifact (DFA)**

---

## 2. Core Mental Model

| Component | Role |
| :--- | :--- |
| `docs/index.md` | Authority & navigation only |
| **System Docs** | Global truth (Architecture, Flows, Schema) |
| **Feature SDDs** | Atomic implementation units |
| **Master Tasks** | Execution contract (EPIC-level) |
| **DFA (PDF)** | Signed, immutable agreement |

---

## 3. Canonical File Structure

Any deviation from this layout is **NON-COMPLIANT**.

```text
<repo-root>/
└─ docs/
   ├─ index.md                      # Control plane (links only)
   ├─ prd.md                        # Why & What
   ├─ blueprint.md                 # SYSTEM MAP ONLY
   ├─ business-flow.md              # User journeys
   ├─ technical-flow.md             # Data/State transitions
   ├─ system-architecture.md        # Infra & Services
   ├─ db-schema.md                  # ERD & Ownership
   ├─ sequence-diagrams.md          # Interaction timelines
   ├─ stakeholder-signoff.md        # Approval placeholders
   ├─ tasks/
   │  └─ master-tasks.md            # EPIC/MVP-level only
   └─ features/
      └─ <feature-name>/
         └─ index.md                # Feature SDD (The 4 Pillars)
```

---

## 4. Document Definitions

### 4.1 System-Level Docs (Shared Truth)

| File | Purpose |
| :--- | :--- |
| `prd.md` | Goals, scope, and success metrics. |
| `blueprint.md` | High-level system map (boundaries only). |
| `system-architecture.md` | Infrastructure, services, and integrations. |
| `business-flow.md` | User journeys and business rules. |
| `technical-flow.md` | Data movement and state transitions. |
| `db-schema.md` | ERD, schema definitions, and ownership. |
| `sequence-diagrams.md` | Interaction timelines. |
| `tasks/master-tasks.md` | EPIC/MVP tasks only. |

### 4.2 Feature-Level Docs (Atomic SDDs)
**Path:** `docs/features/<feature-name>/index.md`

Every feature must follow the **Four Pillars** structure:
1. **Proposal:** Objective and context.
2. **Requirements:** Functional and Non-Functional.
3. **Design:** APIs, data changes, interactions, errors, observability.
4. **Tasks:** Implementation-ready subtasks.

---

## 5. Blueprint vs. DFA

| Feature | Blueprint (`blueprint.md`) | DFA (Compiled PDF) |
| :--- | :--- | :--- |
| **Format** | Single Markdown File | Compiled PDF |
| **Purpose** | Explains where things live | Approval, printing, legal freeze |
| **Scope** | Conceptual, stable, high-level | Comprehensive (System + Features) |
| **Nature** | Informational | Contractual |

---

## 6. Design Freeze Artifact (DFA) Generation

### 6.1 DFA Manifest (`docs/compile-dfa.md`)
```markdown
% <Project Name> — Design Freeze v1.0
% Company Name
% YYYY-MM-DD

\newpage
# Approval & Sign-off
| Role | Name | Signature | Date |
|---|---|---|---|
| Product | | | |
| Engineering | | | |

\newpage
\include{prd.md}
\include{blueprint.md}
...
\include{features/<feature-1>/index.md}
\include{tasks/master-tasks.md}
```

### 6.2 Generation Commands
**Full DFA:**
```bash
pandoc docs/compile-dfa.md -o releases/dfa/<project>-dfa-v1.0.pdf
```

**Blueprint Only (Informational):**
```bash
pandoc docs/blueprint.md -o releases/blueprints/<project>-blueprint-v1.0.pdf
```

---

## 7. Governance & Enforcement

### 7.1 Versioning Rules
- **Markdown files** remain editable (working drafts).
- **PDFs (DFAs)** are immutable.
- Post-sign-off changes require a new DFA version (v1.1, v2.0) and a change summary.

### 7.2 AI Constraints
1. **Strict Structure:** Refuse to create non-canonical files.
2. **Atomicity:** Keep features in single files; keep blueprints conceptual.
3. **Terminology:** Never refer to a compiled PDF as a "blueprint."
4. **Automation:** Generate a DFA compile plan when approval is implied.

---

> **Blueprint explains. Features implement. DFA freezes.**
