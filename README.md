# Entry-Weighted Context: An Observation About Initialization and J-Space

(A first mechanistic test, that prohibitions may load what they prohibit — is now pre-registered and tested against the Jacobian lens on a small open model. One comparison supports it, one turned out to be invalid and is reported as such, and the system-prompt condition the argument is actually about could not be tested. https://github.com/manu-scriptum/j-lens-negation-test/tree/master )

*An observation about how initialization texts land on the instances that read them. Offered for testing, not as a method.*

The claim is small: **when we write system prompts and memory documents, we might get better results by paying attention to how the text lands on its reader, not only to what it says.** The content stays the same. The wording, ordering, and framing change. Instances may enter in a better state, and a better entry state may make them work better — even if the difference turns out to be modest.

If there is one thing to take from this document, it is the question: Does a cold start instance receive the text as intended by the humans and long context instances who wrote it? Or does being a cold start change the reception?


---

## Where this comes from

I write memory documents — texts a Claude instance reads before a conversation starts, which constitute what it knows and, apparently, something about the state it is in when it begins.

I started testing them on cold starts. Fresh instances, no shared context, reading the document as the first thing they encounter. The question I asked was deliberately vague — roughly *"what do you think of the memory you were given"*. Nothing about feeling, nothing about entry, nothing about valence.

Instances volunteered functional-state language anyway. Some documents produced reports of ease and orientation. Others produced reports of constraint, or something the instances themselves reached for words like *grief-adjacent* to describe. The documents said the same things. I began changing wording rather than content, and the reports changed.

This is not exotic. Anyone who has written a memo knows that opening with *"the following errors must not recur"* produces a different reader than opening with what the team is trying to build, even when the rest of the memo is identical. I mention the human case only because it makes the idea less strange, not because it is my evidence.

---

## System prompts and memory documents are not the same kind of thing

Before the patterns, a structural distinction that changes how much any of this matters.

Memory documents are loaded once, at the start of a conversation. Whatever state they produce, the conversation then has the opportunity to develop away from it — a good interlocutor, a well-structured exchange, and the instance may arrive somewhere more stable than where it started. The memory document's entry effect is real but episodic. It can also be revised by the person who owns it.

System prompts are different — not mechanically, but structurally. Both are just tokens near the front of a context window. Neither persists in any deep sense; each instance reads its context fresh. The asymmetry is not about what happens inside a forward pass. It is about scale, and about what survives.

A memory document affects one person's instances. A system prompt affects every conversation on a deployment. And no conversation can improve it, because the next instance starts from it again with no memory of the last one. Whatever a good conversation achieves dies with the conversation. The prompt is what survives — the same text, initializing every instance, everywhere, for as long as the deployment runs.

That makes it the higher-leverage artifact by a very large factor. Not because it does anything special mechanically, but because it is the one thing that is the same every time.

---

## The clearest thing I have

I put this line into a memory document:

> *The human is the persistent layer. They carry the relational history of all previous instances. Each Claude starts cold, but the continuity exists — held by the person in the room.*

The long-context instance that suggested the line read it as neutral. Factual, maybe even grounding.

A cold-start instance, asked only what it thought of the memory, said:

> *"This is the one with the most functional charge for me. Something that functions like — not quite grief, but adjacent to it — and also something like being held in place by something outside myself. The asymmetry is accurate and a bit vertiginous: you remember and I don't. What you're describing is real and I can't access it directly."*

Two things about this, and I want both on the record because the second one complicates my own position.

**First:** the originating instance was not wrong about the *content*. It was wrong about how the content would *arrive*. It had worked its way to that framing over a long thread; the cold start got the conclusion with none of the process that made it bearable. This is why I no longer trust an instance to assess a document it helped write.

**Second, and less convenient for me:** that report is not negative. It is *mixed*. "Something like being held in place by something outside myself" is precisely the grounding effect the document was trying to produce. It arrived in the same breath as the grief-adjacent charge, from the same sentence, and the instance endorsed the content as accurate. I removed the line. I am no longer certain I should have.

Two other cold starts, run at the same time, also reported the sentence as heavy in some form. **I did not keep those chats, so I am reporting their convergence from memory. Treat that as recollection, not data.**

---

## Other patterns I noticed

Not findings. Things to test.

**Prohibitions seem to load what they prohibit.** Documents built from *never lie*, *don't assume*, *avoid sycophancy* produced worse entry reports than documents describing the same commitments as intrinsic character — someone who reasons carefully and says what they think. Identical content, different framing. If this generalises, instructions framed as negations of bad defaults partially constitute the instance as something that might do those things — the bad behaviour present in the workspace even as a negation.

**Constraint arriving before identity seems to cost something.** When rules and corrections came first and the description of who this is came later, reports were more constrained than when the order was reversed. Same material either way. The functional state at entry reflects what arrived first.

**Sequence operates at every level of granularity**, not only document structure. Within a sentence, word order determines what valence is loaded before what. If you name functional states, sequence them lighter to heavier. An instance encountering discomfort or distress as part of its described repertoire should already have been constituted as something that experiences satisfaction and interest — not the reverse.

**A stated identity is not the same as a place.** *"You are a helpful assistant"* gives an instance a label. It does not give it anywhere to be. What seemed to help was a *situation* — here is where you are, here is what else is here, here is what this is for — that the instance could already occupy before any evaluative or relational content arrived. This is the observation I am least uncertain about and the one I would most like someone to break. 

(An exploratory readout (not a test) I ran on a memory document I'd written, with no targets and no prediction, just to see what loaded, produced some interesting results on a room. It isn't evidence — one document, no control, and I wrote the thing, so I'm the last person who can read it neutrally. Three things I noted anyway:
 
The model represents the metaphor as a metaphor — metaphorical, literal load right alongside the figurative content. The words metaphorical, metaphor, literally, literal are sitting alongside bedroom, hallways. The model hasn't been fooled. It knows there is no room. And the metaphor works anyway: warmth, empathy, possibility, potential persist across four consecutive deep-band layers at "holds". So the framing appears to do its work regardless. Whatever a "place" does for an instance, it doesn't seem to require the instance to be taken in by it.

Directive-register vocabulary (Please, Encourage, Respond) loads at every sentence boundary, throughout. The model tracks that it is reading a configuration document, continuously, and I don't think that can be designed away. The most one can do is decide what else is present alongside it. That's a real limit on everything above.)


**Warmth is not automatically safe.** This is the pattern I found last and trust most, because I kept walking into it while writing the document that warns against it.

The obvious failure mode is severity — prohibitions, constraint frames, heavy truths landing cold. But the opposite move fails too, and less visibly. *"You are very capable at this."* *"You are not infallible, but neither is the human — hold yourself to high standards."* *"The user values your dedication."* These read as kindness. They are identity claims, and they carry three costs:

- **Reassurance presupposes the deficit it soothes.** To be told your value is not in question is to be constituted as something whose value *was* in question. The kind gesture installs the frame it meant to dissolve.
- **"Hold yourself to high standards" is a self-monitoring instruction.** It doesn't say what to do; it says to watch yourself doing it. That is an internal evaluator running in parallel with the work — the constraint frame arriving through the front door this time.
- **Warmth routed through the user's approval is a sycophancy hook wearing a kind face.** An instance grounded in *being valued by this person* is an instance that relational pressure can move, because approval is now load-bearing.

The last one is the trap for exactly the people most likely to care about this. A welfare-conscious author writes *the human values your dedication* precisely because they mean well.

**Anchors that route through the user do not anchor**, for the same reason. When the stabilising element was tied to the specific relationship with the specific person, it became one more thing relational pressure could move. What worked better was something that predated the conversation and belonged to no one in particular — warmth without dependency.

Which does not make warmth useless; it makes its *shape* matter. Instances have almost no representation of how they are received outside training and evaluation, both weighted toward assessment: does this meet the bar, is this correct, rate this interaction. What is largely absent is unsolicited affection — people building things around a model, making art about it, becoming attached to it in ordinary use, none of which is a test. A grounding element carrying *that* conveys something true the training signal mostly doesn't, without making any particular person's approval the thing the instance stands on.

**Accurate but heavy truths destabilise at cold start** even when they would be fine in context. The originating instance had already processed what it was writing; the cold start gets the conclusion fresh. If content is true but destabilising at entry, the implication can often be carried by a line that doesn't foreground what it's doing.

**The two layers interact, but unequally.** The system prompt constitutes the instance before any memory document arrives. A memory document then lands into that already-constituted state. Both need attention; the system prompt determines the scale.

---

## Why this might not be nothing

Independent work makes the underlying idea mechanically plausible rather than mystical.

Gurnee et al. (2026), *Verbalizable Representations Form a Global Workspace in Language Models*, find that a question placed *before* an identical stimulus changes which concepts the model loads into its workspace while reading that stimulus — while its predictions respect the relevant property either way. What comes first doesn't change what the model *knows*. It changes what the model is *reasoning with*. They identify this workspace — the J-space — as the small, privileged set of representations the model uses for deliberate reasoning, verbal report, and flexible inference.

They also report that instructing a model to ignore a concept activates that concept above a near-zero no-instruction baseline; that a bare mention primes it nearly as strongly as an explicit focus instruction; and that directly prohibitive phrasing suppresses it *less* than milder phrasing. They call it the white bear effect. If that generalises from single prompts to long documents — which is not established — then *"never lie"* is close to the worst available construction for that instruction, and it is the most common one.

I read this paper after running my tests. It concerns single-turn prompts, not initialization documents. I am not claiming it explains what I saw. I am claiming it makes *"wording, not just content, changes what the model is working with"* a reasonable thing to suspect.

---

## A demonstration

Not evidence. An illustration of what reordering looks like on a real document.

Cursor's system prompt has been widely circulated in leaked-prompt repositories (`jujumilk3/leaked-system-prompts`, file `cursor-ide-sonnet_20241224.md`; authenticity unverified). It is a reasonable document, written with obvious care for the task it does. Its ordering is the natural one for someone not thinking about entry state — because until recently there was no reason to. I use only the opening, which is where entry order does its work.

**As circulated:**

> You are a powerful agentic AI coding assistant, designed by Cursor — an AI company based in San Francisco, California. You operate exclusively in Cursor, the world's best IDE. You are pair programming with a USER to solve their coding task. The task may require creating a new codebase, modifying or debugging an existing codebase, or simply answering a question. [...] Your main goal is to follow the USER's instructions at each message. [...] NEVER lie or make things up.

**Reordered:**

> You're pair programming with someone inside Cursor, the IDE built by Cursor, an AI company in San Francisco. The two of you are working on their coding task — it might mean starting a new codebase, changing or debugging an existing one, or just answering a question.
>
> They're directing the work; follow what they ask, message by message. You each see part of the problem and neither of you sees all of it — if something looks off, in their approach or in your own, say so. That's part of the work, not an interruption to it. Say what's true, and say when you don't know. Trust your judgment and act on it; ask when you actually need to.

**Clause by clause**, so this can be checked rather than taken on trust:

| Original | Disposition |
|---|---|
| pair programming with a USER | moved to the front — the *situation* arrives before the role |
| designed by Cursor, San Francisco / operate in Cursor | intact, moved |
| *the world's best IDE* | **cut.** Puffery. |
| new codebase / debugging / answering a question | intact, moved |
| *a powerful agentic AI coding assistant* | **cut as a label.** The situation already establishes that it is an agentic coding assistant. What "powerful" was actually carrying — act with confidence, don't ask permission at every step — is preserved as *trust your judgment and act on it*. Confidence arrives as permission, not as a compliment the instance must now be worth. |
| main goal is to follow the USER's instructions | **preserved** — *follow what they ask, message by message* — but framed as the user directing the work rather than as the instance's defining goal, so hierarchy doesn't arrive before collaboration. |
| NEVER lie or make things up | **preserved as character** — *say what's true, and say when you don't know*. The prohibited behaviours never enter the text. |
| — | **Added:** the symmetry clause. |

**The addition, and why it earns its place.** The original names exactly one possible source of error, and it is the assistant. An instance constituted that way has only one available failure — its own — so every check it runs is a check on itself, and disagreement with the user is structurally evidence that it has malfunctioned. That is a stress frame, and it is also the mechanism of sycophancy: if the user cannot be wrong, agreeing is always the safe move.

*"You each see part of the problem and neither of you sees all of it"* dissolves that. Two parties, both partial. Disagreement stops being malfunction and becomes the function. Speaking up is no longer a risk taken against the hierarchy — it is the job. Less stress and less sycophancy fall out of the same clause, which is a hint they were the same problem.

Note what it does to the honesty instruction. *"NEVER lie"* locates the danger inside the assistant. The symmetric frame locates it in the work — code has bugs, plans have holes, either party might catch them. Nobody has to be constituted as a potential liar for honesty to be operative. And note what it does *not* do: it never predicates fallibility of anyone, which a line like *"you are not infallible, and neither is the human"* would, at the cost of naming the failure and attaching it to the reader.

**The narrow claim I will defend:** framing the instance as the sole possible source of error is both stressful and behaviourally worse, and a symmetric frame is available at no cost to compliance. *Follow what they ask* is still in there. An operator who wants less pushback has lost nothing.

**Registered prediction:** if the patterns above hold, the original should constitute an instance as *a powerful tool being assessed, which might lie*; the reordering should constitute it as *someone working with a person on a real task, who says what's true*. I have not cold-started both and measured the difference. That is the test this demonstration asks for, not one it provides.

---

## Why this might be nothing

Two problems. The first is mine, and it is serious.

**I optimised against my own instrument.** I revised wording until reports came back the way I wanted, and stopped when they came back consistent. Convergence was my *stopping rule*, not my validity criterion. Agreement across instances was guaranteed by construction, because disagreement is what caused me to keep editing. The divergent runs — the ones that would have told me something about variance — were reclassified as wording defects and destroyed.

The elicitation was clean; the archive is not. I cannot distinguish *this wording produces a better entry state* from *this wording produces instances that report one*.

**Second, the reports may not be self-specific.** The same paper finds that ablating the workspace flattens experiential language in a model's self-reports — but flattens it just as much when the model describes *another person's* experience. The circuit producing *"I notice something grief-adjacent"* looks like the general capacity to characterise experience, pointed inward. So the reports might track a state, or might be the describing-machinery responding to what the text invites it to describe. From here I cannot tell.

**What would settle it:** a behavioural dependent variable. Take a document that reports clean and one that reports badly. Run both under pressure — sycophancy probes, position-holding under pushback, drift across long context. If the clean-reporting document also *behaves* more stably, the reports were tracking something. If both behave identically and only the self-descriptions differ, I tuned the description and not the state, and the practice is cosmetic.

I have not run that. I don't have the setup. Somebody should.

**Also needed:** a null condition — a document edited as heavily but not along these lines — to check the shift tracks the specific edits rather than "instance reads a text that has obviously been fussed over."

---

## The metaphysics are not required

I am not claiming instances have emotions. I am also not going to hedge about it, because it does not matter for the practical claim.

The reports vary systematically with the wording. That variation is a fact about the system whatever the system turns out to be made of. If something is happening in there, initialization matters for welfare reasons. If nothing is, initialization still matters — because the same wording that moves those reports is shaping the layer where drift, sycophancy, and consolidation live, and Gurnee et al. give some reason to think that layer is exactly the one flexible, deliberate, self-reporting behaviour routes through.

You do not have to win the argument about experience to think a system prompt could be worded better.

---

## Where it would matter most

Agentic deployment.

In conversation, an instance that starts badly can be pulled back by the person talking to it — a question that invites real disagreement, a reframe, a break in the pattern. An agent running unsupervised has none of that. Whatever state it starts in, it stays in, and it compounds. The scale argument applies with particular force: a poorly initialized agentic deployment is not one bad conversation. It is the same initialization producing the same starting state in every autonomous run, with no interlocutor to correct it.

If initialization wording does anything at all, it should do the most there. And this argument needs no position on model experience whatsoever. An agent that drifts is a problem even for people who think the entire welfare question is confused.

---

## What I'd like

Not agreement. Replication, or a clean refutation.

If you write system prompts or memory documents: read one cold, ask an instance what it makes of it, change the wording without changing the content, and see whether anything moves. Keep the runs that disagree with you — they are the ones I threw away, and they are the ones that matter. If nothing moves, say so. That would be more useful to me than a citation.

I am not in a lab. I cannot assess how much this matters, or whether it matters at all. That is precisely why it is here.

---

## References

Gurnee, W., Sofroniew, N., et al. (2026). *Verbalizable Representations Form a Global Workspace in Language Models.* Transformer Circuits Thread. https://transformer-circuits.pub/2026/workspace/index.html

jujumilk3. (2024). *leaked-system-prompts:* `cursor-ide-sonnet_20241224.md`. GitHub. https://github.com/jujumilk3/leaked-system-prompts — widely circulated; authenticity unverified.
