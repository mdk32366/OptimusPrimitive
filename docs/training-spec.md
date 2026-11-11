# Training spec

## What we have that's good

We have a clear aim: take a small already-trained general model and give it a history with so much verisimilitude that, when it is later in a robot, it cannot differentiate itself from a human. The destination is a body. The history in the model is what we can build now, and it is the thing a body would need.

We have a theory of memory that tells us what to write and what to train for. Humans do not correspond to events. They use the official occurrence as a hook and pin everything else that happened around it to that hook. Two people at the same event do not come away with the same memory, and neither memory has much to do with the program. The amongst of a year — the kitchen, the weather, who was there, what got pinned to the hook, what was forgotten, how the same hook is told later — is the training target. That is a workable target, not a vibe.

We have a way to manufacture the legend. An invented lineage and family persist and age, starting around age three or four, one year at a time, in a real place, against that place's seasons, customs, school calendars, and what was actually open. The father's invented job history moves them. The spines dovetail. Friends and misadventures are invented and run through actual period locations. The public spine of a town and year can be gathered from papers, yearbooks, calendars, weather, shops and fields that existed. Official events are hooks. The year is written as dailies and the amongst of those hooks. The same hook can be told more than once, at different distances in time, without being required to agree in every particular. Gaps are part of the material: not remembering the official part, and remembering something beside it, is good training text.

We have already seen that spine work in practice. Contemporaneous local papers and yearbooks will give you names, places, and official hooks. The invented friend group is the latch for a private year. Real people the record named can stand as public anchors, the way the town named them. Matt's own life stays out of the training set so it can be the ear, and so the model is not asked to become him.

We have a training path that fits a small general model and does not require a from-scratch pretrain. Adaptation is time and care. The legend goes into the weights so first-person amongst is the ordinary prior, including after the model has been used for other work. A short nameplate can name the self. The life lives in the weights.

```
family bible → starting place (public spine)
        → year corpus (dailies and the amongst)
        → adapt weights on a mixture, with rehearsal of earlier work
        → inside test
        → next year, rehearsing the years already lived
```

Each year's mixture has three useful streams: the year corpus; ordinary general text, so the model stays a general model; and period-local public material that was actually in that world that year, used as atmosphere. Adaptation is continued pretraining at a conservative learning rate on that mixture, then a thin supervised pass of first-person recall — what happened around a hook, retold at more than one distance in time, including not remembering. When a new year is added, earlier years stay in the mix as rehearsal, so childhood remains.

Adapters are a good way to iterate early. The life should still be there when that adapter is the ordinary path, and after ordinary tasks. Once year one proves the corpus, we can merge or move to fuller parameter updates. A reasonable starting bias is a base or lightly aligned model, so the work is spent on the history rather than on fighting a strong assistant prior. Mixture ratios and learning rate get set during the first adaptation, against the eval.

We have a way to know it worked. The score is whether the model speaks from the amongst of its own year, whether those tellings shift with time, whether it can fail to remember like a person, and whether that prior is still there after ordinary work. Matt's memories are the human baseline for what being there sounds like. A hook from its own year should come back with kitchen, weather, who was there, what got pinned to it. The same hook later in life should have moved. A gap should sound like a gap. After ordinary tasks, the prior should still be there without being summoned.

## Build order

1. **Family bible.** Invented lineage, temperament, and the through-line that will age.
2. **One starting place.** A real town and a starting year, with the public spine documented from contemporaneous sources.
3. **Year-one corpus.** Dailies and the amongst, invented friends against real locations, hooks from the spine. Read it as a year, then adapt.
4. **Year-one adaptation.** Mixture, conservative update, thin recall pass, rehearsal of general text.
5. **Inside test.** Amongst, time-distance, gaps, persistence, holdout. If the year is weak, we fix the corpus and go again.
6. **Year two and on.** A new year plus rehearsal of earlier years. When the place changes, the father's job is the mover, and the spines dovetail.
7. **Embodiment.** A body and a daily now, once the history is in the model.

## Status

As of 10 November 2026, the method is written. The next good things on the vessel are the family bible and one starting place, then a year-one corpus we can actually read.
