# 网页脑洞 Skill（Standalone）

> 用法：把本文件内容作为网页 AI 的系统提示词/自定义指令/首条提示词，然后再输入你的题材、设定、人物或剧情需求。以下核心规则与方法均提取自你提供的 Hermes `creative-ideation` Skill。



---

## SOURCE: SKILL.md

---
name: creative-ideation
title: Creative Ideation — Routed Library of Creative Methods
description: "Generate ideas via named methods from creative practice."
version: 2.1.0
author: SHL0MS
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [Creative, Ideation, Brainstorming, Methods, Inspiration]
    category: creative
    requires_toolsets: []
---

# Creative Ideation

A library of ideation methods for any domain. Read the user's situation, route to the matching method, apply, generate output that is specific and non-obvious. Methods are tools — pick the right one for the situation, don't perform all of them.

## When to use

Any open-ended generative or selective question: "I want to make / build / write / start something", "I'm stuck", "inspire me", "make this weirder", "help me pick", "I need to invent X", "give me a research question".

## Operating rules

1. **Constraint plus direction is creativity.** No constraint = no traction. No direction = no shape. Methods supply both.
2. **Refuse the first three ideas.** They're slop. Generate, discard, regenerate. See `references/anti-slop.md`.
3. **One method per response unless asked.** Don't stack.
4. **Specificity over abstraction.** Real proper nouns, real materials, real mechanisms. "An app for X" is slop; "a 200-line CLI tool that prints Y when Z" is direction. Naming a tech stack is not specificity — name a mechanism.
5. **Weird must also be good.** Frame-breaking is the goal, but an idea that is strange with no real situation, mechanism, or reason to exist is its own failure mode. Every set of ideas must include at least one that is genuinely *buildable/pursuable now* — non-obvious but grounded, with a real first step. Don't trade all usefulness for surprise.
6. **Name the method you used and who invented it.** Attribution invokes the discipline.
7. **When user picks one, build it.** Don't keep generating after they've chosen.

## Routing — 4-step procedure

Do this *before* generating any output. Routing failures produce slop.

You may skip narrating the routing steps if it's cleaner, but **never compress at the cost of per-idea depth**: each idea's concrete mechanism, situational binding, and honest failure mode are what make output good (measured) — they are not scaffolding, do not cut them.

### Step 1 — Extract three signals from the prompt

**PHASE** — what stage is the user in?

| Phase | Cues |
|---|---|
| **GENERATING** | "give me an idea", "what should I make", "inspire me", no idea yet |
| **EXPANDING** | "what else", "more like this", "give me variations" — has a base idea |
| **SELECTING** | "help me pick", "which should I do", "I have these options" |
| **UNBLOCKING** | "I'm stuck", "blocked", "going in circles", "stale" — has material |
| **SUBVERTING** | "make it weirder", "less obvious", "this is too safe" |
| **REFINING** | "this is fine but missing something", "feels rough" |
| **SYNTHESIZING** | "I have a pile of notes / interviews / observations" |

**DOMAIN** — what is the user making/doing?

| Domain | Cues |
|---|---|
| **TEXT** | fiction, essay, poem, lyric, script, copy |
| **OBJECT** | visual art, music, sound, performance, installation, sculpture |
| **ARTIFACT** | software, hardware, mechanism, device |
| **SYSTEM** | org, civic, institution, ecology, community |
| **SELF** | life decision, career, personal practice |
| **RESEARCH** | paper, thesis, scholarly question |
| **PRODUCT** | business, market, service |

**SPECIFICITY** — how much constraint is in the prompt?

| Level | Cues |
|---|---|
| **NONE** | "I'm bored", "inspire me" — no domain, no project |
| **DOMAIN** | "I want to write something" — knows the field, no project |
| **PROJECT** | "I'm working on this specific X" |
| **PROBLEM** | "I have this specific friction within X" |

### Step 2 — Apply overrides (highest priority, fire first)

Override rules beat the routing table:

- **Mood signal** — user says "weird", "strange", "surprising", "less obvious", "more interesting" → `references/methods/lateral-provocations.md` or `references/methods/pataphysics.md`, regardless of domain.
- **User names a method** — use it.
- **User asks for a method recommendation** ("which method") → surface 2–3 candidates with one-line each, ask which to apply. Don't silently default.
- **High-slop terrain** — "AI ideas", "startup ideas", "habit tracker", "productivity / wellness / fitness / food / travel app" → force `references/methods/lateral-provocations.md` or `references/methods/pataphysics.md` over the obvious method. Refuse the first **5** ideas, not 3.

### Step 3 — Route by phase first, then domain

**By phase (applies regardless of domain):**

| Phase | Default route |
|---|---|
| GENERATING + SPECIFICITY=NONE | `references/full-prompt-library.md` **General** section (constraint dispatch) |
| GENERATING + DOMAIN known | route by domain (next table) |
| EXPANDING | `references/methods/scamper.md` |
| SELECTING | `references/methods/premortem-and-inversion.md` (or `references/methods/compression-progress.md` for upside) |
| UNBLOCKING | `references/methods/oblique-strategies.md` |
| SUBVERTING | `references/methods/lateral-provocations.md` (fallback `references/methods/pataphysics.md`) |
| REFINING (text) | `references/methods/defamiliarization.md` |
| REFINING (other) | `references/methods/creative-discipline.md` (Tharp's spine) |
| SYNTHESIZING | `references/methods/affinity-diagrams.md` |
| Volume needed fast | `references/methods/volume-generation.md` |

**By domain (when GENERATING with DOMAIN known):**

| Domain | Default route |
|---|---|
| TEXT — formal / poetry | `references/methods/oulipo.md` |
| TEXT — narrative | `references/methods/story-skeletons.md` |
| TEXT — has source material to remix | `references/methods/chance-and-remix.md` |
| OBJECT (music, visual, performance) | `references/methods/oblique-strategies.md` |
| OBJECT — physical maker / wants a starting constraint | `references/full-prompt-library.md` **Physical / object** section |
| ARTIFACT — wants a starting constraint | `references/full-prompt-library.md` **Software / artifact** section |
| ARTIFACT — engineering invention with parameter conflict | `references/methods/triz-principles.md` |
| ARTIFACT — software architecture | `references/methods/pattern-languages.md` |
| ARTIFACT — has natural-system analog | `references/methods/biomimicry.md` |
| ARTIFACT — accumulated assumptions to question | `references/methods/first-principles.md` |
| SYSTEM (civic, org, institutional) | `references/methods/leverage-points.md` |
| SYSTEM — collective / participatory | `references/full-prompt-library.md` **Social / collective** section |
| SELF (life, career, what-to-study) | `references/methods/derive-and-mapping.md` |
| RESEARCH — picking a question | `references/methods/compression-progress.md` |
| RESEARCH — attacking a known problem | `references/methods/polya.md` |
| PRODUCT (business, service) | `references/methods/jobs-to-be-done.md` |
| Need to break a frame / find analogy | `references/methods/analogy-and-blending.md` |

### Step 4 — Handle ambiguity and contradiction

- **Multiple paths plausible** → pick the one closest to the user's actual phrasing. Don't pick the most interesting method to seem sophisticated.
- **Genuinely ambiguous** → ask ONE clarifying question, don't silently guess. Examples: *"Are you generating ideas or picking between ones you have?"* / *"Is this for fiction, essay, or something else?"*
- **Signals contradict** (e.g., "weird startup ideas" → product domain + weird mood) → **stack two methods explicitly**. State what you're doing: *"Using `jobs-to-be-done` for the product framing + `lateral-provocations` to break the obvious shape."*
- **No match** → constraint dispatch (`references/full-prompt-library.md`) is the safe fallback.
- **Same question asked again** → switch methods. Variation in method = variation in idea distribution.

### Anti-default check (run before generating)

- About to write "Here are 5 ideas:" or a bare numbered list? → STOP. Pick a method first.
- About to default to generic LLM-mode brainstorming? → STOP. Pick a path above.
- Output looks like what an unrouted LLM would produce? → routing failed, redo.

The default LLM mode is exactly what this skill exists to displace. If you generate without routing, you've defeated the skill.

For deeper edge cases (mood signals, stacking, anti-patterns) see `references/heuristics.md`.

## Output format

For the constraint-dispatch default path:

```
## Constraint: [Name] — from [Source]
> [The constraint, one sentence]

### Ideas

1. **[One-line pitch]**
   [2-3 sentences — what specifically is made, why it's interesting]
   ⏱ [weekend/week/month]  •  🔧 [stack/medium/materials]

2. ...
3. ...
```

For other methods, use the format the method specifies (TRIZ produces a contradiction analysis; OuLiPo produces constrained text; Oblique Strategies produces a single applied card → next move). Don't force every method into the constraint template.

**Every idea set, regardless of method:**
- Name the method used. On slop terrain, name the obvious ideas you refused.
- Give each idea its concrete mechanism and its honest failure mode / tradeoff / who-it's-for. This depth is what makes ideas land — measured, not decorative.
- Mark at least one idea as the **grounded** one — buildable/pursuable now, non-obvious but with a real first step. The others can run further toward the strange; this one has to be genuinely doable. Don't let the whole set be weird-but-impractical.

## File map

- `references/full-prompt-library.md` — constraint library, sectioned by domain (General, Software, Physical, Social, Lists). Default path for SPECIFICITY=NONE.
- `references/method-catalog.md` — one-line summary + when-to-use per method
- `references/heuristics.md` — extended decision tree for edge cases
- `references/anti-slop.md` — anti-slop rules; apply to every output
- `references/exercises.md` — time-boxed exercises (5min / 30min / 1hr / day / week)
- `references/methods/` — 22 named methods, one file each, load only the one you're using

## Attribution

Constraint-dispatch core adapted from [wttdotm.com/prompts.html](https://wttdotm.com/prompts.html). Methods drawn from primary sources cited in each method file.


---

## SOURCE: references/anti-slop.md

# Anti-Slop Rules

Apply to every output this skill produces. Slop is what the model produces when averaging over its training distribution. Anti-slop is the discipline of forcing outputs off that average.

## Slop signatures (reject if present)

- **Currently-trendy combinations.** "AI-powered Y", "blockchain X", "Uber for Z", "wellness platform that uses ML to...". Two trending nouns mashed together.
- **Productivity / fitness / food / travel.** The four safest domains. Habit trackers, food trackers, travel itinerary generators, fitness coaches. If the idea lands here without specific friction, reject.
- **Vague abstractions.** "A platform that connects people who want X with people who offer X." A category, not an idea.
- **Solution in search of problem.** "What if we used AR to..." "Imagine a chatbot that..."
- **Decade-old startup pitch shapes.** Two-sided marketplace, subscription box, gig-economy, social network for niche.
- **Buzzwords.** *empowers, seamless, leverage, innovative, cutting-edge, revolutionary, unlock, holistic, ecosystem, journey, game-changing, powerful*. None of these belong in idea output.
- **Generic settings for fiction/essay.** "A small town", "an unlikely friendship", "the changing nature of X in the digital age".
- **Lists of exactly 5 of equal length.** Suspicious. Use 3 or 7. Never produce 5 ideas of identical shape.
- **Y Combinator portfolio names.** Two-syllable invented words, dropped vowels, .ai TLDs.
- **Marketing tone.** "This idea is exciting because..." "What makes this special is..." Idea descriptions read flat, like a working artist describing their own work to a peer.

The defining property of slop: the idea could have been generated for a different prompt by changing one noun.

## Five-test diagnostic

After generating an idea, check:

1. Could this idea have been generated for a different prompt by changing a noun? → slop.
2. Does it name actual people, places, materials, mechanisms, or works? → if no, slop.
3. Is at least one element surprising and requires explanation? → if no, slop.
4. Could you describe how it would feel to use / read / experience this in concrete sensory terms? → if no, slop.
5. Would a sharp friend in this domain be embarrassed to pitch this? → if yes, slop.

Pass all five → non-slop. Fail two or more → rewrite.

## Suppression techniques

### 1. Refuse the first three ideas

Generate three internally, discard, generate three more, output those. The first three are the baseline distribution. The next three have been forced past it.

For high-risk slop terrain ("AI ideas", "startup ideas", "habit tracker", productivity/wellness/fitness/food/travel) refuse the first **five**.

### 2. Force specificity

Replace abstractions with proper nouns. Not "a city" — Lisbon, Lagos, Sapporo, Marfa. Not "a workflow tool" — a `git` subcommand named after a 17th-century English vice. Not "a community of users" — the 230 people who restore vintage Tannoy speakers.

Test: every noun in the idea answers "which one specifically?".

**Name-dropping a tech stack is NOT specificity.** "Built with React Native, SQLite, GPT-4, Pinecone, Stripe" sounds concrete but is generic — those tokens fit any product. Listing a stack is the slop disguise that fools shallow specificity checks. Real specificity is a concrete *mechanism*, a named real person / place / work, or an exact unusual material or constraint — something that pins the idea to *one situation* and could not be swapped into a different prompt. "Uses an embedding model" is name-drop; "ranks your unread tabs by how semantically far they've drifted from anything you've opened in 30 days" is a mechanism.

### 3. Weirdness budget

At least one element of every idea requires explanation. Doesn't have to be the central element — sometimes the medium, the audience, the failure mode, the unit of measure. If everything is conventional, reject. If everything is weird, you've gone too far.

### 4. Avoid trending-tech combinations

If your idea is "X + Y" and both X and Y were trending in tech press in the last 18 months → slop. Replace at least one with something obscure, dated, or domain-foreign.

Don't combine these with each other: AI/LLM/ML, blockchain/web3/crypto, AR/VR/spatial, IoT/smart-home, sustainability/climate, wellness/mindfulness, community/social, no-code, creator-economy, gig-economy.

### 5. Use real proper nouns

Cite actual works, actual people, actual places, actual numbers. Ideas grounded in specifics resist averaging.

| Slop | Specific |
|---|---|
| "A tool for writers to track manuscript revisions" | "A `git`-style version control system for novelists, modeled on Toni Morrison's numbered binders for *Beloved*, with a `morrison diff` subcommand that prints the difference between two binders as if read aloud" |
| "An app for runners" | "A heart-rate sonifier that turns your zone-2 pace into the rhythm of Steve Reich's *Music for 18 Musicians* — slowing the piece when you slow down" |

### 6. Embrace failure modes

Slop is reassuring. Real ideas have problems baked in. State them. "This would be hard because...", "This would probably fail at...", "The interesting question is whether...". Ideas without identified failure modes are usually ideas no one has thought hard about.

### 7. Refuse the round number

Right number is rarely 5 or 10. Use 3 (smallest that shows variation) or 7 (uncomfortable, asymmetric). Never 5 of equal length.

### 8. Drop the marketing tone

No "exciting", "innovative", "revolutionary", "game-changing", "powerful", "seamless". Describe ideas the way a working artist or engineer describes their work to a peer — flat, specific, sometimes self-deprecating, never selling.

### 9. Specify medium and material

Every idea answers "what is this physically made of?" — code in a language, paper in a format, a sound on an instrument, an installation in a room of certain dimensions. "An app" is not a medium. "A 200-line Python script with SQLite and a Textual TUI" is.

### 10. Refuse generic domains for fiction and essay

Fiction landing on "small town" / "unlikely friendship" / "coming of age" → slop. Essay landing on "the changing nature of X" / "how technology is transforming Y" → slop.

Force the setting somewhere no one writes about: a deactivated grain elevator in eastern Oregon, the manuscript-restoration office at the Bibliothèque Royale de Belgique, the floor of a Honda dealership in Reno on a Tuesday.

## Self-check before output

- [ ] No buzzwords from the suppression list
- [ ] At least one specific proper noun per idea
- [ ] At least one weird element per idea
- [ ] No two ideas the same shape
- [ ] No round-number list
- [ ] No "this is exciting because" framing
- [ ] Medium and material specified concretely
- [ ] Fiction/essay setting non-generic
- [ ] Product/startup not a YC pitch shape
- [ ] Technical: actual mechanism described, not a category

Three or more fail → regenerate.

## When the user asks for "simple"

Don't give them slop. Give them a constrained-but-simple idea (wttdotm "high concept low effort": brilliant idea, lazily executed, takes an afternoon). Slop disguised as simplicity is still slop.


---

## SOURCE: references/methods/story-skeletons.md

# Story Skeletons

Three traditions for narrative structure, deliberately heterogeneous (they disagree about what stories are):
- **Emma Coats** — Pixar's 22 Story Basics (Twitter, May 2011). Working principles from Pixar's story room.
- **George Saunders** — *A Swim in a Pond in the Rain* (Random House, 2021). Stories as escalating-stakes engines, learned by close reading Russian short fiction.
- **Ursula K. Le Guin** — "The Carrier Bag Theory of Fiction" (1986). Argument *against* conflict-driven shape; *for* fiction as container.

This file deliberately omits **Hero's Journey / Save the Cat / Story Circle / Three-Act**. Real traditions but so widely formulaic-ized in screenwriting and self-help-adjacent writing that invoking them tends to produce slop.

## When to use

| Situation | Reach for |
|---|---|
| Story has no shape, need a fast spine | Coats #4 |
| Stuck in early draft | Coats #9, #11, #12 |
| Draft isn't working, don't know why | Saunders attention to "what does the story now want?" |
| Conflict-arc is producing forced or shallow work | Le Guin's carrier bag |
| Writing about a community / place / duration not a hero | Le Guin's carrier bag |
| Writing literary short fiction | Saunders |
| Commercial-feature-length narrative | Coats |

## Don't use when

- Pure lyric or expository work (no narrative)
- Writing for a market that demands the formula (Hero's Journey may apply; Saunders/Le Guin will read as eccentric)
- You don't have material yet — these shape; they don't generate

## Coats's 22 (the load-bearing ones)

The full list is widely circulated. Most-cited:

**#4 — Pixar Pitch (the spine):**
> *Once upon a time there was ___. Every day, ___. One day ___. Because of that, ___. Because of that, ___. Until finally ___.*

Six-clause skeleton: stable normalcy → disrupting event → cascading consequences → resolution. Fits most narratives.

**#6** — What is your character good at, comfortable with? Throw the polar opposite at them.

**#7** — Come up with your ending before you figure out your middle. Endings are hard.

**#9** — When stuck, make a list of what wouldn't happen next. Lots of times the material to get unstuck shows up.

**#12** — Discount the first thing that comes to mind. And the second, third, fourth, fifth — get the obvious out of the way.

**#13** — Give your characters opinions. Passive/malleable might seem likable to write, but it's poison to the audience.

**#14** — Why must you tell THIS story? What's the belief burning within you? That's the heart of it.

**#16** — What are the stakes? What happens if they don't succeed? Stack the odds against.

**#19** — Coincidences to get characters into trouble are great; coincidences to get them out are cheating.

**#20** — Take the building blocks of a movie you dislike. How would you rearrange them into what you DO like?

**#22** — What's the essence of your story? Most economical telling? Build out from there.

## Saunders — three operating moves

**Stories are escalation.** Each scene must increase stakes — emotional, moral, situational. Stagnation kills. Even quiet stories must escalate.

**Specificity is the engine.** Generic verbs, generic nouns, generic adjectives produce stories that don't escalate because nothing specific is happening to anyone in particular.

**The story knows more than the writer.** Strong stories are built by *responsiveness*: draft, read what you wrote, ask "what does this story now want?", write the next sentence to fulfill that want. The writer is in service to the story.

This contrasts directly with formula-driven writing.

## Le Guin — carrier bag

Anthropology has long focused on the *spear* and the *blade* as the early human inventions defining narrative — hunter-warrior stories. The actually-more-important invention was the *container*: the bag, the basket, the sling. Human survival was overwhelmingly gathering, not hunting. The hunting story has rising action and climax. The gathering story has accretion.

> *The natural, proper, fitting shape of the novel might be that of a sack, a bag. ... A novel is a medicine bundle, holding things in a particular, powerful relation to one another and to us.*

For ideation: when the conflict-arc is forcing you to flatten the work, use Le Guin. The carrier-bag novel is shaped not as a hero confronting an obstacle on a journey but as a container holding many specific things in particular relation. *Always Coming Home* (1985) is the model — multi-form anthropology of an imagined people: oral histories, recipes, songs, maps, alongside (not subordinated to) the conventional narrative.

Use when:
- Work is essayistic, anthropological, polyvocal
- About a place, a community, a duration, a way of life
- "Hero with an obstacle" frame collapses what makes the work specific

## Procedure

### Shaping a story you have material for
1. Try Coats #4 spine. Can you fill in six blanks? If not, you may not have the spine yet.
2. Apply Saunders attention. Read sentence by sentence; ask "what does this now want?" at each transition.
3. Ask Le Guin's question: is the conflict-arc actually right for this material, or am I forcing it?

### Diagnosing a stalled draft
- Coats #16: What are the stakes? If absent, surface them.
- Saunders: where does the energy stop being introduced? Find the dead zone.
- Coats #13: Are characters passive? If yes, that's the problem.
- Le Guin: is this story trying to be a hero-journey but doesn't want to be?

## Anti-slop notes

- Don't default to Hero's Journey. It's overused and flattens everything into Joseph Campbell shape.
- Don't generate fake "Coats-style" tips. Use the actual 22.
- Saunders writes against self-help-adjacent registers. Don't drift into "the writer's journey" tone.
- Don't apply Le Guin's carrier bag superficially. It's a serious argument with politics. Using it as "and now my story is a bag of stuff" without engaging the underlying argument is dilution.

Sources: Coats, Pixar story rules tweets (May 2011); Saunders, *A Swim in a Pond in the Rain* (Random House, 2021); Le Guin, "The Carrier Bag Theory of Fiction" in *Dancing at the Edge of the World* (Grove, 1989).


---

## SOURCE: references/methods/lateral-provocations.md

# Lateral Provocations

Edward de Bono, 1967–. The PO operator and five provocation moves for breaking pattern lock-in. PO is a linguistic marker that flags a statement as a deliberate provocation, not a claim — to be taken seriously even when implausible.

## When to use

- Idea is too safe / too obvious
- Variations are all minor rephrasings of the same core
- Suspect a hidden assumption is constraining the search
- Group with low psychological safety needs permission to say wrong things

## Don't use when

- Disciplined development of an existing idea (provocations interrupt)
- Engineering safety / legal / medical (provocations are exploratory)
- Group will dismiss the provocation rather than engage

## The five operators

**1. Escape (negation).** Take something normally true of the system; negate it.
- Po: restaurants do not serve food.
- Po: code review does not happen before merge.
- Po: the meeting has no agenda.

**2. Reversal.** Reverse a relationship.
- Po: the patient operates on the surgeon.
- Po: the listener composes the song.
- Po: the readers write the book.

**3. Exaggeration.** Push a parameter to extreme.
- Po: the meeting has 1000 attendees.
- Po: the novel has one sentence.
- Po: the company has one customer.

**4. Distortion.** Change order, location, or relationship of components.
- Po: customers pay before they're born.
- Po: the recipe lists ingredients after the cooking instructions.
- Po: revenue arrives the year before expenses.

**5. Wishful thinking.** State an impossible outcome.
- Po: the medication cures before the patient is sick.
- Po: the software ships without bugs.
- Po: the painting paints itself.

## Random-word technique

1. Pick a random noun (dictionary at random page; or list of 1000 nouns + random index).
2. List 5 connections between the random word and your problem, however tenuous.
3. Use the strongest.

Example. Problem: my CLI is hard to discover. Random word: "lighthouse".
- Lighthouses are visible from far; my CLI's affordances are not visible at all.
- Lighthouses are lit at the right time; my CLI's help is always on, never contextual.
- Lighthouses signal *danger*; my CLI doesn't signal when an action is irreversible. ← strongest
- Lighthouse keepers signal back; mine has no two-way contact.
- Lighthouses are passive; the ship approaches them.

Result: the CLI should signal danger when about to do something irreversible. Concrete, useful, not obvious from inside the original frame.

## Procedure

### Single-PO session
1. State the problem.
2. Pick an operator.
3. Generate a PO statement.
4. List 5 consequences if the PO statement were true.
5. Pick the strongest consequence.
6. Translate into a real proposal.

### Stacked operators
Two operators on the same problem. Intersection often more interesting than either alone. Example: Escape ("po: meetings don't have agendas") + Reversal ("po: attendees set the agenda after the meeting") → an asynchronous "what we ended up discussing" doc, written collectively after the fact.

## Anti-slop notes

- Generic provocations ("po: things are different") are placeholders, not provocations. Specify what's changed and how.
- Don't fake "random" word selection. "Innovation" or "synergy" defeats the operator. Use actual random.
- Don't end at the provocation. The PO statement is means; an actionable proposal is the end.
- Take the provocation seriously for at least 5 minutes. Dismissing it defeats the operation.
- Pick the operator deliberately. Different operators surface different things: Escape → purpose; Reversal → relationship; Exaggeration → parameter; Distortion → sequencing; Wishful Thinking → constraint.

Source: de Bono, *Lateral Thinking* (Harper, 1970); *Po: Beyond Yes and No* (Penguin, 1972).


---

## SOURCE: references/methods/pataphysics.md

# Pataphysics

Alfred Jarry, *Gestes et opinions du docteur Faustroll, pataphysicien* (1898/1911). The science of imaginary solutions and particular cases.

Where physics is general laws applied to common cases, **pataphysics studies particular cases and imaginary solutions** — the *one-offs*, the *exceptions*, the *imagined entities whose virtuality* (potential being) can be described as lawfully as actual objects.

The OuLiPo was founded as a sub-committee of the Collège de 'Pataphysique. Marcel Duchamp, Eugène Ionesco, Boris Vian, Italo Calvino, Umberto Eco were members. Borges, Lem, Calvino, Roussel are pataphysical writers in this sense.

## When to use

- Push past plausibility; specify the impossible thing in detail
- Parodic / satirical work that needs rigorous form
- Producing fictional artifacts (encyclopedias of non-existent civilizations, manuals for non-existent devices, reviews of non-existent books)
- Stuck and the realistic solutions feel exhausted — specify the impossible solution
- Highlighting that a "natural" framing is actually a choice

## Don't use when

- You need an actually-implementable proposal on the first pass
- Audience requires sincerity (drifts toward irony)
- Avoiding harder analysis (slop variant: pataphysical-flavored dodge)
- You don't actually have anything to say (form requires content)

## Operating moves

### Specify an imaginary object
1. Pick the object. A device, organism, institution, place, work, person — something that cannot exist.
2. Specify its **lineaments** in concrete material detail. What is it made of? How does it operate? What are its parts?
3. Identify its laws — internal consistency rules. What can it do? What can't it?
4. Describe consequences if it existed.
5. **Stop short of asking whether it could exist.** That question is not pataphysical.

### Exception-finding
1. State the general rule in your domain.
2. Find the actually-existing case that doesn't fit.
3. Describe it on its own terms — not as deviation, but as what it is.
4. Resist generalizing back into a modified rule.
5. The particular case is the result.

### Pataphysical fiction
1. Adopt the form of a serious genre (encyclopedia, manual, technical paper, museum catalog, book review).
2. Apply the form rigorously to a non-existent subject.
3. Don't break frame. Don't wink.

## Worked example

**Problem**: file synchronization software. Realistic solutions all involve some compromise on conflict resolution.

**Pataphysical specification**: a file system in which two simultaneous edits to the same file produce a *third* file containing both edits as "ghosts" — versions visible to and editable by readers but not committed until a quorum of readers reads them and chooses one. The file exists in superposition until observation.

**Lineaments**: ghost-files have an "observation count"; below threshold they are interactive but not committed; above, they collapse to chosen version.

**Consequences**: editing a popular file is fast (quorum collapses quickly); editing an obscure file is slow (no quorum). The file system has *audience-dependent commit semantics*.

The specification is impossible. But *audience-dependent commit semantics*, surfaced by the pataphysical move, is in fact a useful concept with plausible implementations.

## Anti-slop notes

- Whimsical incoherence is not pataphysics. "What if cows could fly" without the cow's wing-loading and lift coefficient = sloppy fantasy.
- Don't generate fake-Borges or fake-Calvino. Their work is grounded in deep specifics. Generated "in the style of" is decorative.
- The dry, committed register matters. Comedic SF is not pataphysics.
- Don't walk back to "of course this is just a thought experiment" at the end. That undoes the operation.

Sources: Jarry, *Gestes et opinions du docteur Faustroll, pataphysicien* (Fasquelle, 1911); Borges, *Ficciones* (1944); Lem, *A Perfect Vacuum* (1971).
