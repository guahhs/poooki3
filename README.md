# Application Essay Studio

A Claude Agent Skill for reviewing, stress-testing, restructuring and drafting
university and scholarship application essays. Built for international
applicants to Japanese English-medium programmes, and general enough for
Western holistic admissions.

Nothing about a specific programme is stored in this skill. Prompts, word
limits, curricula and institutional values are fetched at the time of use,
because they change every cycle and stale data is worse than none.

## Install

**Claude Code, from a marketplace**

```
/plugin marketplace add YOUR-GITHUB-USERNAME/aes-plugin
```

```
/plugin install application-essay-studio@application-essay-studio
```

**Claude Code, as a personal skill**

Copy `skills/application-essay-studio/` into `~/.claude/skills/` (or into a
project's `.claude/skills/` to scope it to that repository).

**claude.ai**

Upload `application-essay-studio.skill.zip` at `claude.ai/customize/skills`.

## What it does

Six modes, which compose: `review`, `excavate`, `restructure`, `committee`,
`draft`, `set-audit`.

**Four ordered passes.** Order is load-bearing — line-editing a draft whose
theme has not landed is wasted work, so a failed structural verdict stops the
line pass.

1. **Administrative** — word count in *both* directions, compound-prompt clause
   coverage, eligibility and programme-name mismatches.
2. **Accuracy** — four layers, because most factual failures are not false
   statements: truth, metric match, scope, mechanism. Plus institutional-credit
   claims verified at the time of the achievement, and an interview-defensibility
   list.
3. **Structure** — a thirteen-dimension rubric, evidence quoted before any score.
   Includes the two mechanical substitution tests: swap the institution's name,
   and trace the motive-preparation-future chain.
4. **Line** — What / Why / How, where How is a worked fix or a labelled slot
   template.

**The committee.** Five differentiated readers plus a sixth seat that attacks
the panel's own scoring rather than the essay. It rejects by default: a file
advances only on an affirmative case, because plenty of essays are clean and
forgettable. It never declares an essay finished — each round reports what
changed, what is still broken, and what the remaining gap costs, so the
applicant decides.

Role separation here is a **coverage device, not an independence device**.
Personas do not produce independent judgement; what does the work is independent
passes pooled afterwards, side-by-side comparison, an adversary aimed at the
evaluation, and precise localisation instead of grading.

## What it refuses to do

- Invent a course, professor, lab, award or motivation. Specifics the applicant
  has not supplied are left as labelled slots.
- Penalise class-marked material. Service, caretaking, part-time work and
  tutoring correlate *against* household income; treating them as mundane
  encodes class bias as craft advice.
- Deduct for genericness without naming the sentence and asking the question
  that would de-generalise it. Convergence toward generic prose is concentrated
  among applicants with the least editing help.
- Edit to defeat AI detection. Detectors are not accurate enough on short texts
  for that to be a coherent goal, and the real penalty attaches to prose that
  reads as interchangeable.
- Flag "I realized" as a defect per se, cite per-application reading-time
  figures, or claim the essay is decisive. Each of those is either contested in
  the published guidance or traceable only to consultancy marketing.

## Layout

```
skills/application-essay-studio/
├── SKILL.md                          workflow, modes, ten invariants
└── references/
    ├── rubric.md                     thirteen dimensions, anchored
    ├── committee.md                  six seats, round protocol
    ├── japan-english-medium.md       genre conventions, research plans
    ├── fact-check.md                 the four layers
    ├── drafting.md                   beat spine, slot scaffold, prose
    └── excavate.md                   interview mode, no draft needed
```

`SKILL.md` carries only the workflow and the invariants; the reference files
load when the relevant pass runs. The invariants sit in the first third of the
body deliberately: in Claude Code an invoked skill retains only its first ~5,000
tokens after context compaction, and a long multi-round review session is
exactly where the rules that prevent ghostwriting would otherwise fall out of
context.

## Caveats worth knowing

The anti-inflation rules for multi-round critique are engineering inference, not
established findings — no study measures score inflation across rounds of an LLM
critique loop. The rubric's scale anchors are drafting practice, not a validated
instrument; there is no inter-rater-reliability study of admissions-reader essay
ratings, so treat scores as a device for forcing specificity rather than as
measurement.

The accuracy pass depends on network access. On the Claude API's skill container
there is none, and on claude.ai it depends on account settings. Where it cannot
run, the skill reports claims as `unverified` rather than answering from memory.

Programme rules on generative AI are set **per programme**, not per university,
and they are heterogeneous. Check the one you are applying to.

## License

MIT. See `LICENSE`.
