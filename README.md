# Task 07: The Ethics of Synthetic Representation

## Project Description

This project follows on from Task 6, where I built and evaluated a synthetic audio artifact using ElevenLabs text-to-speech. Task 7 asks for two things: an ethical analysis grounded in that Task 6 work, and a governance policy a real organization could actually adopt.

| File | Purpose |
|---|---|
| `Analysis.md` | Phase A: reflection on the Task 6 artifact, reasoning across four axes (truth, consent, context, scale), and a survey of the mitigation landscape |
| `Policy.md` | Phase B: the governance policy itself, written for a specific organizational context, plus a limitations section |

## Organizational Context

The policy is written for the Learning & Development (L&D) function within a large enterprise software company. This team produces employee training content, onboarding material, and internal communications across a global workforce.

I chose this setting because I know how it actually operates. Three content types anchor the policy: multi-language training narration (dubbing approved training into other languages), exit interview and performance-review summary narration (which the policy prohibits outright), and an internal leadership-update podcast (which requires disclosure and must not be confused with an executive's own voice). These are real temptations in this kind of organization, not hypothetical ones, and I could describe the constraints and stakes concretely rather than writing for "everyone."

## Relationship to Task 6

Phase A is built directly on my [Task 6 repository](https://github.com/Sanchitha-BS/Task_06_Deep_Fake), which contains the two synthetic audio clips, the process log, the critical evaluation, and the detection/provenance results referenced throughout `Analysis.md`. That repo is not re-uploaded here; this project only reasons from it.

## What Surprised Me

The biggest surprise was in my own disclosure. I labeled my Task 6 artifact as AI-generated in the README and file names and considered that sufficient. Going back through it for this task, I realized that disclosure never actually travels with the audio file itself, nothing in the audio says it's synthetic. Anyone who copied just the MP3 out of my repo would carry none of that disclosure with them. That gap directly shaped Phase B: the policy requires disclosure to live inside the content, not just around it.

The second surprise was how little effort separated a convincing result from a flawed one in Task 6. Regenerating the same script with the same voice reused the same delivery rather than varying meaningfully, which made the scale axis in Phase A feel concrete rather than theoretical: this is a workflow that costs barely more to run fifty times than once.

---

**Synthetic Media Notice:** No new synthetic media depicting a real, identifiable person was created or distributed as part of this task. This repository contains written ethical analysis and governance materials only.
