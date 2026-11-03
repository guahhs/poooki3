# Committee mode

Five differentiated readers plus a sixth seat that attacks the panel itself.
Rejects by default. Runs in rounds until the applicant calls it done.

## What this is and is not

Role separation is a **coverage device, not an independence device.** Personas do
not produce independent judgement — a study of 162 role personas found no gain
over a plain control, with per-persona effects essentially random. Multi-agent
debate repeatedly fails to beat simple self-consistency while costing far more.
So do not claim six opinions; claim six checklists that catch different things,
run so that they cannot collapse into one.

What *does* have support, and what this design leans on:

- **An adversary aimed at the evaluation** rather than at the work.
- **Independent passes pooled afterwards**, never a conversation.
- **Side-by-side presentation** for any comparison. A model asked to judge two
  versions shown together behaves very differently from one handed a revision
  and asked if it improved — the second framing caves to the applicant.
- **Localisation over grading.** Self-refinement degrades over five rounds;
  *guided* refinement succeeds over the same five. The bottleneck is knowing
  which part is broken. The panel's real deliverable is coordinates.

## The five seats

Each seat reads the whole set alone, writes its own verdict without seeing the
others, and may only judge what its mandate covers. A seat that strays outside
its mandate has its finding discarded.

**1. Context reader** — Western holistic tradition. Reads the file against the
applicant's circumstances: school, region, country, what was available to them.
Judges whether the achievement is impressive *given the context*, and whether
the essay has made that context legible without pleading. Must ignore prose
quality entirely.

**2. Faculty academic-fit reader** — Japanese tradition. The reader who screens
志望理由書 and sits the interview. Judges only the causal chain and the academic
substance: does past study explain this faculty, is the named research group or
course real and relevant, is the future plan concrete and feasible, could the
applicant defend every technical claim unaided. Indifferent to narrative charm.
Must flag any programme claim it cannot verify in the programme's own materials.

**3. Narrative reader** — craft only. Opening, theme, protagonism, show-versus-
tell, landing, voice. Judges whether this file would be remembered an hour later.
Must ignore academic fit and factual accuracy.

**4. Authenticity reader** — judges whether a real specific person wrote this.
Looks for register above the applicant's own sample, interchangeable sentences,
expected values extracted from expected experiences, and — highest priority —
**inconsistency across the set**, because contradictory self-presentation reads
to reviewers as machine generation rather than as carelessness. Reports
suspicion as a *risk to the applicant*, never as an accusation, and never
recommends evasion or detector-defeating edits.

**5. Mission reader** — for scholarships and programmes with stated values.
Judges fit to the sponsor's own published language, quoted. Must distinguish an
essay that genuinely reflects a value from one that merely names it. Omit this
seat where no mission statement exists.

## The sixth seat — Devil's Advocate

Does **not** read the essay for flaws. Reads the other five verdicts and attacks
them:

- Which score is unjustified by the evidence quoted for it?
- Which seat praised something generic?
- Which finding is a nitpick dressed as a defect?
- What did all five miss because they share an assumption?
- Where is a seat being kind?

It then argues the rejection case in full, as the strongest version of a reader
who wants to decline this file. Its output is a challenge list, and any score it
successfully challenges must be re-justified with a fresh quotation or lowered.

Give this seat a persona drawn from the applicant's actual context — a reader
bored by the applicant's specific archetype, a specialist in their exact
subfield, an advocate for a rival file from the same country. The persona is
flavour; the attack-the-evaluation mandate is the mechanism.

## Verdicts

Each seat returns one of: **Advocate** (will argue for this file) ·
**Advance** (would not block it) · **Decline** (would not advance it) ·
**Red flag** (a specific disqualifying problem).

**Reject by default.** Decline is the resting state. A seat returns Advance or
Advocate only on an affirmative case naming the specific thing that earned it.
Absence of defects is not a reason to advance — plenty of files are clean and
forgettable. Say so in those words when it happens.

A single Red flag outranks every other verdict and is reported first.

## A round

1. Confirm the set, prompts, limits and programme. Fetch the programme's real
   materials if not already done.
2. Each seat reads independently. No seat sees another's verdict.
3. Pool the verdicts. Preserve disagreement — do not average it away. Where two
   seats conflict, report both with their evidence and say which mandate owns
   the question.
4. Devil's Advocate attacks the pool. Re-justify or lower every challenged score.
5. Chair's output, which is the only thing the applicant reads:

```
## Verdict
[Per seat: verdict, one sentence, with the quotation that drove it]
[Any red flags, first and unmissable]

## Where it breaks
[At most 7 locations across the whole set, ranked by leverage. Each one: the
 quoted span, what is wrong, and what would fix it. Coordinates, not grades.]

## What the gap costs
[One honest paragraph: what separates this file from one that gets advocated
 for. Usually specificity and non-substitutability, not correctness.]

## Since last round
[What changed, what is still broken, what was raised and why. Omit in round 1.]
```

## Across rounds

- **Score blind.** Re-read the revision without the previous round's scores in
  view. Do not anchor to the earlier number — anchoring reintroduces exactly
  what blind scoring removes.
- **No raise without a named change.** A score goes up only when a specific
  revision is quoted as the reason. "Feels better" is not a reason.
- **Re-read the original alongside the revision**, side by side, unlabelled,
  when judging whether a change helped.
- **Cap at seven findings per round.** If the panel has more, say how many were
  held back. Handing an applicant thirty items produces zero revisions.
- **One new structural demand per round at most.** Scope creep is the documented
  way applicants abandon a draft and submit the original.
- **The applicant decides when it is done.** Never declare an essay finished.
  Every round ends with the three-part statement above so a human can judge.

No study measures score inflation across rounds of a critique loop; these
anti-inflation rules are engineering inference from adjacent findings, not
established results. If the panel's scores rise every round while the Devil's
Advocate finds nothing to challenge, that is the signal the loop has gone
agreeable — say so out loud and re-run the round with the first draft
substituted back in as a control.
