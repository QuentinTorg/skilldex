# Review Feedback Categorization Template

*Present this template exactly as formatted. Do not omit the code context or the agent's evaluation reasoning.*

## 📊 Summary
- **Total Comments:** [X]
- **Address Now:** [X] | **Defer to Issues:** [X] | **Decline/Do Nothing:** [X]

---

## 🟢 Category: Address Now
*(These are critical issues, or small changes that simplify the diff.)*

### 1. [Comment Title / Short Summary]
- **Author:** [@username]
- **Implementation Risk:** [Low / Medium / High]
- **Impact/Importance:** [Low / Medium / High]
- **Agent's Evaluation:** [Brief reasoning on *why* this is the assigned risk and impact, based on PR intent.]
- **Reviewer Comment:**
  > "[Exact quote of the review comment]"
- **Code Context:**
  ```[language]
  // [Lines N-M of file/path.ext]
  [surrounding code snippet showing what the comment refers to]
  ```

---

## 🟡 Category: Defer to Issues
*(These are style/cleanup, nice-to-haves, or items out of the PR's original scope.)*

### 2. [Comment Title / Short Summary]
- **Author:** [@username]
- **Implementation Risk:** [Low / Medium / High]
- **Impact/Importance:** [Low / Medium / High]
- **Agent's Evaluation:** [Brief reasoning on why this should be deferred (e.g., out of scope of the PR's intent).]
- **Reviewer Comment:**
  > "[Exact quote]"
- **Code Context:**
  ```[language]
  // ... snippet ...
  ```

---

## 🔴 Category: Decline / Do Nothing
*(These are misaligned goals, incorrect feedback, or mere observations that require no code change.)*

### 3. [Comment Title / Short Summary]
- **Author:** [@username]
- **Agent's Evaluation:** [Brief reasoning on why this is being declined or just acknowledged.]
- **Reviewer Comment:**
  > "[Exact quote]"
- **Code Context:**
  ```[language]
  // ... snippet ...
  ```