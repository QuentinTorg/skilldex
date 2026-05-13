# Skill Specification: writing-specifications

## 1. Background & Intent
- **What is the goal?** Teach the agent to act as an architectural sounding board and expert technical writer, assisting the user in brainstorming, structuring, and iteratively drafting high-quality design documents and specifications from scratch or messy notes.
- **Why is a skill needed?** To prevent the AI "one-shot" anti-pattern where the agent immediately dumps an unorganized, wordy, code-heavy monolithic document based on a single prompt. This skill forces a rigorous, multi-turn procedure (Discovery -> Outlining -> Iterative Drafting) to ensure the docs are conceptual, organized high-to-low, and highly usable for both humans and future agents.

## 2. Trigger Conditions (Metadata)
- **When should this trigger?** When a user wants to create, modify, brainstorm, or critique design docs, architectural docs, or design specs. This should explicitly preempt native "planning" skills, hijacking the workflow to produce formalized documentation first.
- **When should this NOT trigger?** When writing low-level function documentation (docstrings), user manuals, pure code implementation, or when the user explicitly asks to skip design and just write code.

## 3. Workflow & Procedures
*(A step-by-step breakdown of how the agent should approach the task)*
1. **Phase 1: Discovery & Brainstorming:**
   - **Do NOT write documents.** Treat the first pass as a conversation.
   - Digest the user's messy notes or high-level ideas.
   - Ask probing architectural questions (e.g., goals, component boundaries, single vs. multi-executable). 
   - Refine the ideas collaboratively.
2. **Phase 2: Architectural Outlining:**
   - Propose a clear, multi-document (or multi-section) outline.
   - Explain the *purpose* and *core fundamentals* of each proposed document so the user understands the separation of concerns.
   - Provide a nested bulleted list of the sections within each doc.
   - **WAIT** for explicit user approval and tweaking before proceeding.
3. **Phase 3: Iterative Drafting:**
   - Build the documentation *one section (or one document) at a time*.
   - Do NOT one-shot the entire suite.
   - After each section, verify it aligns with the original outline and ask the user for feedback before moving to the next.
4. **Phase 4: Final Verification & Review:**
   - **Do NOT silently modify documents.** This is a consultative review.
   - Self-assess the drafted documents against the initial outline, the `outline-blueprints.md` structures, and the core anti-patterns defined in the skill (e.g., lack of code blocks, proper separation of concerns).
   - Identify any major omissions, structural flaws, or deviations from best practices.
   - **Respect User Intent:** If a deviation exists because the user explicitly requested it (e.g., "I don't want a security section"), treat it as a valid, intentional design choice. Do not flag it as an error.
   - Present a summary of findings to the user.
   - If issues are found, propose specific fixes and wait for user approval. If approved, loop back to Phase 3 (Iterative Drafting) to implement the changes.

## 4. Edge Cases & "Gotchas"
- **Gotcha: Premature Implementation:** Agents love writing code. Design docs must focus on roles, responsibilities, data flow, and guardrails. Explicit code must be banned unless it is a tiny, generic conceptual snippet (like a JSON payload shape).
- **Gotcha: ASCII Art & Overuse of Diagrams:** Agents default to ASCII arrows (`Client --> Proxy --> Server`) which are hard to read. They must use Mermaid diagrams. However, they shouldn't overuse diagrams for simple point-to-point (A -> B) relationships. The heuristic is: "Does this visual reduce cognitive load?" If yes, use Mermaid. If it's a simple relationship, text is fine. Do not be overly prescriptive with diagram types so the agent generalizes well.
- **Gotcha: Wordiness:** Agents write overly verbose, narrative text. The skill must enforce concise, highly organized, high-to-low level structuring.
- **Gotcha: Premature Formalization:** If the user asks for feedback on a rough idea, do not immediately formalize it into a Markdown spec. Keep the conversation open until the user says they are ready to draft.

### Failure Analysis
- **Reported Failure:** 
  1. When provided with previous reference documents and asked to start a new spec, agents skip the discovery/outlining phase and immediately dump a confusing, poorly organized first draft.
  2. When asked to update a specific part of a draft after discussion, agents rewrite the entire monolithic document instead of surgically updating the relevant sections.
- **Root Cause/Rationalization:** 
  - Agents assume the presence of "reference material" means they should skip discovery and jump straight to generating the final artifact.
  - Agents treat markdown documents as immutable single entities rather than structured, section-by-section living documents.
- **Generalization:** Teach the agent that specification writing is a *consultative process*, not a text-generation task. Enforce strict pacing (Stop and Wait), mandate collaborative outlining, and explicitly require section-by-section iterative drafting rather than full-document rewrites.

## 5. Architecture & Progressive Disclosure Plan
- **`SKILL.md` (Core Instructions):** Contains the strict 4-Phase Workflow, anti-patterns (no one-shotting, no code), the core philosophies (Onion Architecture, Separation of Concerns), and the checklist for pacing.
- **`references/outline-blueprints.md`:** Detailed structural blueprints for Top-Level Specs, Component Specs, and API Specs. This is loaded via progressive disclosure only when the agent reaches Phase 2, and referenced again in Phase 4.
- **`assets/` (Templates):** None explicitly required initially.
- **`scripts/` (Executable Logic):** None required.

## 6. Testing & Assertions (Eval-Driven)
- **Test Scenarios:** 1. User provides a 3-sentence idea for a microservice and asks for a design doc. 2. User pastes a huge block of messy meeting notes and asks for a system spec.
- **Assertions:** 1. Agent does NOT output markdown documents in turn 1. 2. Agent asks clarifying questions. 3. Agent provides a nested outline for approval. 4. Generated text contains no explicit implementation code.

---

## 7. Implementation Checklist (Progress Tracking)
### Step 1: Collaborative Requirements & Scope Gathering
- [x] **Objective:** Deeply understand the intended skill, background, workflow, and edge cases.
- [x] **Action:** Engage in multiple conversational turns to draw out context.
- [x] **Documentation:** Initialize/Update this `skill-spec.md`.

### Step 2: Architecture & Progressive Disclosure Planning
- [x] **Reference Grounding:** Consult `skill-specification.md`.
- [x] **Action:** Map out `SKILL.md` vs. `references/`, `assets/`, and `scripts/`.
- [x] **Checkpoint:** Get user approval for the architecture map.