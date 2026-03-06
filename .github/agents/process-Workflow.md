# Agentic Workflow Template

**Workflow Name:** [Workflow Name]
**Version:** 1.0
**Owner:** [Your Name]
**Last Updated:** [Date]
**Status:** Draft | Active | Paused | Retired

---

## Table of Contents

1. [What This Workflow Does](#1-what-this-workflow-does)
2. [How to Use This Template](#2-how-to-use-this-template)
3. [Your Requirement](#3-your-requirement)
4. [The Plan](#4-the-plan)
5. [Workflow Steps](#5-workflow-steps)
6. [Tests — The Rules the Workflow Must Pass](#6-tests--the-rules-the-workflow-must-pass)
7. [First Run — Build & Test](#7-first-run--build--test)
8. [Every Run After That](#8-every-run-after-that)
9. [When Something Goes Wrong](#9-when-something-goes-wrong)
10. [Run Log](#10-run-log)
11. [Notes & Decisions](#11-notes--decisions)


## steps to follow when creating a new workflow. 
---
  1. ask user about the workflow they want to create. Get as much detail as possible about what they want, why they want it, and how they will use it.
  2. All workflows **must** be implemented as a **Python-based project**. Set up the project with the following standard structure:
     ```
     workflow-<name>/
     ├── main.py            # Entry point — orchestrates the workflow steps
     ├── steps/             # One .py module per workflow step
     │   └── step_1.py
     ├── tests/             # pytest test files, one per step / test case
     │   └── test_step_1.py
     ├── requirements.txt   # Python dependencies (include pytest by default)
     └── README.md          # Brief description and usage instructions
     ```
  3. Use **pytest** for all tests (listed in `requirements.txt`). Tests must be runnable with `pytest tests/`.
  4. Every step defined in Section 5 must map to a function in `steps/` and have at least one corresponding test in `tests/`.
  5. The workflow is not considered complete until `pytest tests/` passes with no failures.
---


---

## 1. What This Workflow Does

> This template helps anyone — no technical knowledge needed — describe what they want done, turn it into a clear step-by-step workflow, write simple tests to make sure it works, and run it reliably every time.
>
> **The golden rule:** Tests run first. Green = go. Red = fix, then go.

---

## 2. How to Use This Template

Follow these four stages in order — every time you set up a new workflow:

```
STAGE 1 — DESCRIBE   →   Write your requirement in plain English (Section 3)
STAGE 2 — PLAN       →   Break it into steps (Section 4 & 5)
STAGE 3 — TEST       →   Define what "working correctly" looks like (Section 6)
STAGE 4 — RUN        →   Execute, check tests, fix if needed, then run (Sections 7 & 8)
```

You only do Stages 1–3 once. After that, every execution follows Stage 4.

---

## 3. Your Requirement

> Write what you want this workflow to do in plain, everyday language. No jargon. Pretend you are explaining it to a friend.

### In One Sentence
[e.g. "Every Monday morning, collect last week's sales numbers, check they look right, and email a summary to the team."]

### More Detail
[Add any extra context here. Who triggers this? How often? What are the inputs? What should the output look like?]

### Inputs (What goes IN)
| # | Input | Description | Example |
|---|-------|-------------|---------|
| 1 | [Input name] | [What it is] | [Example value] |
| 2 | [Input name] | [What it is] | [Example value] |

### Outputs (What comes OUT)
| # | Output | Description | Example |
|---|--------|-------------|---------|
| 1 | [Output name] | [What it is] | [Example value] |
| 2 | [Output name] | [What it is] | [Example value] |

---

## 4. The Plan

> Before building the workflow, write a plain-English plan. Think of this as a checklist of intentions.

### Goal
[One sentence: what does success look like when this workflow finishes?]

### Assumptions
- [Thing you are assuming to be true, e.g. "The input file will always be a CSV"]
- [Assumption 2]
- [Assumption 3]

### Constraints
- [A rule the workflow must follow, e.g. "Must complete within 5 minutes"]
- [Constraint 2]

### Plan Steps (Plain English)
1. [First thing that needs to happen]
2. [Second thing]
3. [Third thing]
4. [And so on…]

---

## 5. Workflow Steps

> This is the strict, ordered sequence the workflow must follow every single time. Do not skip steps. Do not reorder steps.

### Step Map

```
START
  │
  ▼
[STEP 1] ──────────────────────────────── [What happens here]
  │
  ▼
[STEP 2] ──────────────────────────────── [What happens here]
  │
  ▼
[STEP 3] ──────────────────────────────── [What happens here]
  │
  ├── IF something goes wrong ──────────► [Go to Section 9: Fix Process]
  │
  ▼
[STEP 4] ──────────────────────────────── [What happens here]
  │
  ▼
END ✓
```

### Step Detail

#### Step 1 — [Step Name]
- **What it does:** [Plain description]
- **Who or what does it:** [Person / tool / system]
- **Input needed:** [What this step needs to start]
- **Output produced:** [What this step hands to the next step]
- **Python module:** `steps/step_1.py` — function `run(input) -> output`
- **Must complete before:** Step 2

---

#### Step 2 — [Step Name]
- **What it does:** [Plain description]
- **Who or what does it:** [Person / tool / system]
- **Input needed:** [What this step needs to start]
- **Output produced:** [What this step hands to the next step]
- **Must complete before:** Step 3

---

#### Step 3 — [Step Name]
- **What it does:** [Plain description]
- **Who or what does it:** [Person / tool / system]
- **Input needed:** [What this step needs to start]
- **Output produced:** [What this step hands to the next step]
- **Must complete before:** Step 4

---

#### Step 4 — [Step Name]
- **What it does:** [Plain description]
- **Who or what does it:** [Person / tool / system]
- **Input needed:** [What this step needs to start]
- **Output produced:** [Final output]
- **Must complete before:** END

---

## 6. Tests — The Rules the Workflow Must Pass

> Tests are simple yes/no checks. Before the workflow runs, every test must pass. If any test fails, the workflow stops, fixes the problem, and re-tests before continuing.
>
> **Think of tests as your safety net.** They catch problems before they cause damage.

### How to Read the Test Table

| Column | Meaning |
|--------|---------|
| ID | A unique code for this test (e.g. T-01) |
| Test Name | Short friendly name |
| The Check | Exactly what is being verified, in plain English |
| Pass Condition | What "green" looks like |
| Fail Condition | What "red" looks like |
| Blocking? | YES = workflow cannot run if this fails. NO = warning only. |

---

### Test Suite

| ID | Test Name | The Check | Pass ✅ | Fail ❌ | Blocking? |
|----|-----------|-----------|--------|--------|-----------|
| T-01 | [e.g. Input exists] | [e.g. Check the input file is present] | [e.g. File found] | [e.g. File missing] | YES |
| T-02 | [e.g. Input is valid] | [e.g. Check the file is not empty and has the right columns] | [e.g. All columns present] | [e.g. Missing columns] | YES |
| T-03 | [e.g. No duplicate records] | [e.g. Check there are no repeated rows] | [e.g. 0 duplicates] | [e.g. 1+ duplicates] | YES |
| T-04 | [e.g. Output destination reachable] | [e.g. Check the email address / folder / API is accessible] | [e.g. Reachable] | [e.g. Unreachable] | YES |
| T-05 | [e.g. Previous run completed] | [e.g. Check the last run finished cleanly] | [e.g. Status = Done] | [e.g. Status = Failed] | NO |

> Add as many tests as you need. More tests = more confidence.

---

### Test Result Log

Fill this in every time tests are run.

| Date & Time | Run # | Tests Passed | Tests Failed | Failed IDs | Action Taken |
|-------------|-------|-------------|-------------|------------|--------------|
| [Date] | 1 | [#] | [#] | [e.g. T-02] | [e.g. Fixed input file, re-ran] |
| | | | | | |

---

## 7. First Run — Build & Test

> The very first time you run this workflow, follow this exact sequence. This is the only time you build and test simultaneously.

```
FIRST RUN SEQUENCE
══════════════════

 ① WRITE the workflow steps (Section 5) ────────────── Done? [ ]

 ② WRITE the tests (Section 6) ─────────────────────── Done? [ ]

 ③ RUN all tests
      │
      ├── ALL PASS? ──► Continue to ④
      │
      └── ANY FAIL? ──► Fix the problem (see Section 9)
                        Re-run ALL tests
                        Repeat until all pass

 ④ EXECUTE the workflow (follow Section 5 steps exactly)
      │
      ├── SUCCESS? ──► Mark Run #1 as ✅ in the Run Log (Section 10)
      │                Save this workflow. It is now ACTIVE.
      │
      └── FAILURE? ──► Record the failure in Section 10
                       Fix the problem (see Section 9)
                       Return to ③ and repeat

```

---

## 8. Every Run After That

> Once the workflow is ACTIVE, follow this shorter sequence every time.

```
STANDARD RUN SEQUENCE
══════════════════════

 ① RUN all tests (Section 6)
      │
      ├── ALL GREEN ✅ ──► Proceed immediately to ②
      │
      └── ANY RED ❌ ────► STOP. Do not run the workflow.
                           Fix the failing test(s) — see Section 9.
                           Re-run ALL tests.
                           Only continue when ALL tests are green.

 ② EXECUTE the workflow (follow Section 5 steps exactly, no shortcuts)

 ③ CHECK the output matches what Section 3 describes

 ④ LOG the run in Section 10

```

> **Key principle:** The workflow steps are fixed. You do not improvise or skip. If something seems wrong mid-run, stop, log it, and go to Section 9.

---

## 9. When Something Goes Wrong

> Something failed. Stay calm. Follow this process.

### Fix Process

```
SOMETHING FAILED
      │
      ▼
 ① STOP immediately — do not continue the workflow

 ② IDENTIFY what failed
      • Which step failed? (Section 5)
      • Which test failed? (Section 6)
      • What was the exact error or wrong result?

 ③ RECORD it in the Fix Log below

 ④ DIAGNOSE the root cause
      • Is the input wrong or missing?
      • Did a step produce the wrong output?
      • Did an external system (email, file, API) not respond?

 ⑤ FIX the root cause
      • Do NOT patch over the symptom
      • Fix the actual cause

 ⑥ RE-RUN ALL TESTS (not just the failed one)

 ⑦ If all tests pass ──► Return to the start of the run sequence
    If tests still fail ──► Return to ④ above

```

### Fix Attempt Limit
> If you have attempted to fix the same problem **3 times** without success, escalate. Do not keep trying the same fix. Get help or reconsider the workflow design.

### Fix Log

| Date | Run # | Failed At | Error Description | Root Cause | Fix Applied | Fix Worked? |
|------|-------|-----------|-------------------|-----------|-------------|-------------|
| [Date] | [#] | [Step / Test ID] | [What went wrong] | [Why it went wrong] | [What you changed] | YES / NO |
| | | | | | | |

---

## 10. Run Log

> Record every execution here — successes and failures alike.

| Run # | Date & Time | Triggered By | Tests Result | Workflow Result | Notes |
|-------|-------------|-------------|-------------|----------------|-------|
| 1 | [Date] | [Name / Schedule] | ✅ All pass / ❌ [#] failed | ✅ Success / ❌ Failed | [Any notes] |
| 2 | | | | | |
| 3 | | | | | |

---

## 11. Notes & Decisions

> Use this section to capture anything important — why a decision was made, a change in requirements, a lesson learned.

| Date | Note |
|------|------|
| [Date] | [e.g. Changed Step 2 to include validation after T-02 kept failing in early runs] |
| | |

---

## Quick Reference Card

> Cut this out and keep it handy.

```
┌─────────────────────────────────────────────┐
│         WORKFLOW QUICK REFERENCE             │
├─────────────────────────────────────────────┤
│                                             │
│  FIRST TIME SETUP                           │
│  1. Write steps  (Section 5)                │
│  2. Write tests  (Section 6)                │
│  3. Run tests → fix if red                  │
│  4. Run workflow → log result               │
│                                             │
├─────────────────────────────────────────────┤
│                                             │
│  EVERY RUN                                  │
│  1. Run tests                               │
│     ALL GREEN → run workflow                │
│     ANY RED   → fix first, then re-test     │
│  2. Run workflow (follow steps exactly)     │
│  3. Check output                            │
│  4. Log the run                             │
│                                             │
├─────────────────────────────────────────────┤
│                                             │
│  IF SOMETHING BREAKS                        │
│  1. Stop immediately                        │
│  2. Record the failure                      │
│  3. Fix root cause                          │
│  4. Re-run ALL tests                        │
│  5. Only proceed when all green             │
│  6. Max 3 fix attempts → escalate           │
│                                             │
└─────────────────────────────────────────────┘
```

---

*This template is designed to be used by anyone. If a section is confusing, rewrite it in your own words — clarity matters more than following the format exactly.*
