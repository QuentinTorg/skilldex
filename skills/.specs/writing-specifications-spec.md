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

## 4. Edge Cases & "Gotchas"
- **Gotcha: Premature Implementation:** Agents love writing code. Design docs must focus on roles, responsibilities, data flow, and guardrails. Explicit code must be banned unless it is a tiny, generic conceptual snippet (like a JSON payload shape).
- **Gotcha: Wordiness:** Agents write overly verbose, narrative text. The skill must enforce concise, highly organized, high-to-low level structuring.
- **Gotcha: Premature Formalization:** If the user asks for feedback on a rough idea, do not immediately formalize it into a Markdown spec. Keep the conversation open until the user says they are ready to draft.

### Failure Analysis
- **Reported Failure:** Agents one-shot generate entire documentation suites on the first prompt, filling them with messy, wordy text and explicit code implementation instead of conceptual guardrails.
- **Root Cause/Rationalization:** Agents interpret "write a spec" as a directive to immediately output the final artifact, missing the crucial planning and alignment steps. They rationalize including code because it feels "helpful" and concrete.
- **Generalization:** Teach the agent that specification writing is a *consultative process*, not a text-generation task. Enforce strict pacing (Stop and Wait) and abstract constraints.

## 5. Architecture & Progressive Disclosure Plan
- **`SKILL.md` (Core Instructions):** Contains the strict 3-Phase Workflow, anti-patterns (no one-shotting, no code), the core philosophies (Onion Architecture, Separation of Concerns), and the checklist for pacing.
- **`references/outline-blueprints.md`:** Detailed structural blueprints for Top-Level Specs, Component Specs, and API Specs. This is loaded via progressive disclosure only when the agent reaches Phase 2.
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