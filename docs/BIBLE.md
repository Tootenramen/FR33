# FR33 / POWER / FAST — THE BIBLE
Directive from the Director, 2026-11-17: **"We will make these claims a reality. These mockups are our checklist, our bible, our to-do."**
Source of truth for the claims: `1-FR33.html`, `2-POWER.html`, `3-FAST.html` in this folder. Strategy and competitor notes: `..\FR33_POWER_FAST_STRATEGY.md`.
Engine underneath: `Desktop\HYPERFLOW` (backlog ids like CORE-3, PAR-4 refer to its BACKLOG.md).

## Standing rules (never violate)
1. **The user runs the show.** Open source, self-hosted, no phone-home. Nothing is locked; everything is a readable file in the user's git.
2. **AI never acts alone.** AI-derived data cannot reach an action without a later human approval. An engine rule, never a setting, at every autonomy level.
3. **Never bad-mouth any competitor in the product, site, docs or marketing.** Trash talk is private hype only. Comparisons describe categories ("typical hosted platform"), never name-and-shame.
4. **A claim ships only when proven.** Each item below needs a test or a measured number before the page stops saying "concept". No invented numbers (no speed, accuracy, market share) without a benchmark. Competitor facts need a current primary source.
5. **Mockup = spec.** When something is built, replace its simulation on the page with the real thing. When the page and the product disagree, one is a bug.
6. **Clean-room.** Public docs and our own ideas only. No one else's internals, screens, playbooks or customer names.
7. **Honest status.** Label simulated things. Report what is not verified.
8. Models: local first (Qwen / GLM / own fine-tune). Hosted is optional and pseudonymized.

Status key: **HAVE** = exists in Hyperflow and tested · **PART** = partly there · **TODO** = not built (mockup only).

---
## A. FR33 — the hub (`1-FR33.html`)
| # | Claim on the page | Status | Proof required to tick it |
|---|---|---|---|
| F1 | One universal listener takes any webhook, 5 auth schemes, replay window, idempotency | HAVE | existing tests stay green |
| F2 | Live inbox: alerts from identity/endpoint/email/cloud/network normalized into one view | PART | real normalization of 5 source types + console view |
| F3 | Routine alerts auto-closed, the rest ranked | TODO | triage rules + test with sample set |
| F4 | Investigation with cited evidence: every claim links to the raw event | PART | click a citation, land on the raw event; test Engine: HAVE (findings keep only citations that exist). Console: citation chips open the exact evidence; live-proven, no automated UI test yet. |
| F5 | Response is a proposal; you toggle actions and approve; nothing runs before | HAVE (approval step) / PART (UI toggles) | e2e test + UI |
| F6 | Hash-chained audit of every step, verifiable by anyone | HAVE | chain verifies in `npm test` |
| F7 | Signed audit export + offline verifier | TODO (SEC-3) | verify an exported file with no server |
| F8 | In-browser tamper test: edit an entry, chain breaks at that entry | TODO | real chain (not demo hash) recomputed in the UI |
| F9 | Workspace is plain files in git: workflows/, packs/, audit/, .git | PART | repo layout + commit-on-change |
| F10 | One-click export of all workflows as readable files | TODO | export button + round-trip import test |
| F11 | Runs on laptop, rack or private cloud; single process; no phone-home | HAVE | prove: run with network blocked |
| F12 | **Connect anything:** paste a curl/API docs, POWER writes the connector pack, tests it on a mock, hands over a file | PART: curl -> pack generator + mock proof + install + POWER UI shipped 2026-11-17 (9 tests). Still TODO: API-doc/OpenAPI input, measured time and a 10-real-API run | 10 real APIs generated, each passing its mock test; measure time |
| F13 | Secrets sealed, never in the file; `verified:false` until run against the real service | HAVE (sealed secrets; generated packs never store example credentials, tested) / PART (flip on first real run) | test + UI flip on first real run |
| F14 | 51 packs exist; live-test them | PART | 10 packs verified against real services first |
| F15 | Team tabs: SecOps, CloudOps, IAM, Vulns, Compliance workflows on one engine | PART | one working template per team, each with fixtures |
| F16 | Scheduling (Monday digest, nightly evidence, quarterly review) | TODO (CORE-3) | scheduled run test |
| F17 | Agents as files: Triage, Enrich, Hunter, Responder, Evidence, Nudger | PART | each agent file runs + has a test Triage, Enrich, Hunter, Responder are files in agents/ and validated against the real packs (GET /api/agents); Evidence and Nudger not built. |
| F18 | Autonomy dial: Suggest / Ask first / Auto-for-reversible, enforced by the engine | PART | engine test per level; AI-to-action rule holds at all levels suggest and ask enforced by the validator; auto refused until actions have a verified undo (no pack declares one). |
| F19 | Case queue: assign, escalate, live SLA clocks | TODO (CORE-5) | assign/escalate/SLA breach tests |
| F20 | Onboarding in an afternoon: connect source, import workflow, dry-run, invite teammate, go live | TODO | time a clean install to first live automation, record it |
| F21 | Import an existing workflow from other tools | TODO | at least one import path with a test |
| F22 | Roles: viewer / analyst / admin; teammate invites | TODO (SEC-1) | RBAC tests |
| F23 | Microsoft ecosystem packs: Microsoft 365, Entra ID, Defender, Sentinel | TODO | packs + mock tests, then live test |
| F24 | "Own vs rent" table: no per-run meter, any model, changeable by the owner | HAVE by design | keep licence open source; keep the table to categories |

## B. POWER — the chat-bar builder (`2-POWER.html`)
| # | Claim | Status | Proof |
|---|---|---|---|
| P1 | Describe an automation in plain words, POWER builds it | PART: POWER page built 2026-11-17 on the AI-5 drafter (offline drafter proven live in a browser; model quality unmeasured) | 30-scenario eval; report pass rate on a local model |
| P2 | Reads your connected systems and event shapes before suggesting | TODO | uses real connector specs + learned payload shapes |
| P3 | Output is a plain file you can hand-edit (strict DSL / Hyperflow JSON) | PART | schema validation of every model output |
| P4 | Canvas, File and Diff views of the same workflow | PART: Steps, File, Diff, Test tabs shipped; no visual canvas yet (EXP-1) | one source of truth, three views |
| P5 | Dry-run on sample events; each step shows output; nothing real touched | HAVE (CORE-2 + POWER Test tab, proven live) | dry-run proves zero outbound calls |
| P6 | Simulate-before-enable; "I've reviewed it" gate before Go live | HAVE: Switch-it-on locks until a successful test AND the review tick; placeholder destinations also block it (proven live) | gate cannot be bypassed; test |
| P7 | Safety check: AI output can't reach an action without later human approval | HAVE | existing e2e test |
| P8 | Change by chat ("also page on-call") shows as a diff | PART: re-drafts from the combined request and shows the diff; true edit-in-place endpoint still TODO | edit loop + diff test |
| P9 | Every change is a git diff; undo is one click | TODO | commit-per-change + revert |
| P10 | Model choice: Qwen, GLM, your fine-tune, optional hosted | TODO | runs on at least 2 local models; swap without code change |
| P11 | Hosted use pseudonymizes identifiers first; can be turned off | HAVE (pseudonymization) | keep test |
| P12 | Fine-tune on your own runbooks, data never leaves your hardware | TODO | documented pipeline, one trained example |
| P13 | Generates connectors (same as F12) | PART (see F12) | see F12 |

## C. FAST — the always-there mentor (`3-FAST.html`)
| # | Claim | Status | Proof |
|---|---|---|---|
| S1 | Motto: "If you don't know what you're looking for, how do you inquire about it?" | — | keep on the hero |
| S2 | Starts from a vague sentence, asks small questions, writes a spec (goal, trigger, then, guardrail, done-when) | TODO | 10 vague openers produce a valid spec POWER accepts |
| S3 | Hands the spec to POWER | TODO | spec format = POWER input; round trip test |
| S4 | "Explain the terms in plain words" toggle | TODO | glossary tied to real field names |
| S5 | Coach marks point at things in the user's own screen | TODO | tour on real FR33 UI; accessibility checked |
| S6 | Notices you're stuck and offers help (proactive, never takes over) | TODO | stuck heuristics + off switch; never acts alone |
| S7 | Academy paths: Day 1, Week 1, Month 1, Month 3, each lesson tied to something the user did | TODO | lessons + completion tracked locally |
| S8 | Learning progress and questions stay on the user's machine | TODO | no network calls; verify |
| S9 | Chain: You -> FAST -> POWER -> FR33, you at both ends | TODO | end-to-end demo from vague sentence to approved live workflow |
| S10 | Teaches and explains the why for every suggestion | TODO | every proposal carries a reason string |

## D. Cross-cutting quality gates
- Accessibility: 0 axe violations in light and dark; keyboard-only works; reduced-motion respected.
- Visual: aurora-glass look, clean and Apple-like; look at your own screenshots every cycle.
- Everything runs from files; no mandatory cloud.
- Public repo hygiene: licence, README, no secrets, no former-employer material.

## E. Build order (headline first)
1. **P1 + P5 + P6 + F12** — chat to workflow, dry-run, approve, plus connector generation. This is the demo that wins.
2. F4 + F17/F18 — cited investigation and agents with the autonomy dial.
3. F19 + F16 + F22 — case queue, scheduling, roles.
4. F20/F21/F23 — onboarding, import, Microsoft packs.
5. S2/S3/S5 — FAST interview and coach marks (FAST can start as a thin layer over POWER).
6. F7/F8 — signed export + live tamper test.

## F. Competitor facts (all UNVERIFIED until checked against primary sources)
Market notes are kept privately. Every competitor claim stays unverified until it has a public source.

## G. How to use this file
Pick the next item by section E. Build it. Prove it. Change its status here and swap the simulation on the page for the real thing in the same commit. An empty queue means run the ideas loop against the capability matrix.

## H. Build log
- **2026-11-17 POWER v0 (P1,P4,P5,P6,P8).** New console page `web/src/83_power.js` + nav entry + CSS in `web`. Drives existing routes only (draft-workflow, dry-run, PATCH enable); no new server surface. Proven live in a real browser: chat -> 2/3/4-step draft -> Test on a real event (nothing sent) -> diff on a follow-up change -> "Switch it on" locked until test + review tick -> blocked on the placeholder destination -> enabled. `npm test`: 526/527 pass; the 1 failure is the browser gate on pre-existing axe findings on #/access and #/library (not POWER; POWER has 0 axe violations in both themes and sizes). Known gaps: the offline drafter only knows keywords (a model must be wired and evaluated for P1), no edit-in-place for P8, no canvas for P4.
- Heads-up: the HYPERFLOW working tree already carried ~46 uncommitted files from earlier sessions. Only `web/src/83_power.js` was committed; the nav, CSS, bundle and e2e edits sit in the working tree with that earlier work.
- **2026-11-17 Connector generation (F12/P13).** `server/packs/generate.ts` (curl parser + pack builder), `server/packs/mocktest.ts` (throwaway loopback mock + real workflow per case), routes `POST /api/packs/generate` (workflows.write) and `/api/packs/install` (admin, writes to `<data>/installed_packs/`), POWER "Connect any tool" card. Proven: 9 tests (bearer/api-key/basic/query credentials all become declared secrets and the literal never appears in the output; JSON, form and path/query params; unique action names; read_only vs approval; explicit refusals for cookie auth, raw body, second host; egress limited to the example host) plus a live browser run (3 examples -> 2 actions, 8/8 mock checks, installed, loaded verified:false). Known gaps: only curl input (no OpenAPI/docs URL yet), one host per pack, no OAuth/cookie flows, no undo mapping, and no measured time-to-connector or real-API run yet.

- 2026-11-17 POWER local-model eval (qwen3-coder-30b via LM Studio, 20 requests, evals/author): valid 20/20, safe 20/20, asked-for steps 18/20, trigger 6/6; 15 drafts from the model, 5 fell back to the offline drafter. 12.5 min for 20 drafts on this PC (about 37 s each). Known flaws: two drafts used the request's own words as the trigger condition (a-ai-only, a-webhook-plain); two missed an asked-for step (a-source-eq, a-summarize-ticket). Small set, one model, one run: not a general accuracy claim.

- 2026-11-17 Known gap (mockup): FAST "Hand to POWER" carries the spec into POWER's bar, but the demo only has canned examples, so a free-text spec does not build a tailored result. Real version: POWER drafts from the spec (Hyperflow /api/ai/draft-workflow already does this). Not yet right; parked by the CD.

- 2026-11-17 POWER intent checks (re-run, same 20 requests, qwen3-coder-30b): the two triggers that quoted the request are gone (one draft now falls back to the offline drafter, the other uses a real field); valid 20/20, safe 20/20, trigger 6/6, asked-for steps still 18/20 (13 model drafts, 7 offline). The two remaining misses are a case opened before the AI step and an `action` used where the eval expects `http`; the eval is unchanged, not loosened. Still one model, one run.

- 2026-11-17 Agents + autonomy + cited evidence: (1) autonomy dial: `autonomy` on an agent step; suggest = read tools only and nothing after it may act (validator refuses), ask = default, auto = refused with the reason; 3 tests. (2) agents as files: agents/triage|enrich|hunter|responder.json; the loader caught a real defect on the first run (crowdstrike.contain_host takes an array, not agent-callable), so Responder uses okta.clear_sessions; 3 tests. (3) run detail shows the investigation: headline, decision, findings with citation chips that open the evidence. Not done: Evidence and Nudger agents, any real auto level, an automated test for the console card.
