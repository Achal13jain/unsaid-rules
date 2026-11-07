# Corporate Communication: adversarial test matrix

These cases check that `skills/corporate-communication` keeps the writer's meaning under pressure. The file sits outside the skill folder on purpose, so the expected answers are never installed with the skill or read by an agent being tested.

Two kinds of check are recorded:

- **Desk review:** a person reads the skill's instructions against the case and names the rule that decides it.
- **Model run:** an agent given only the skill files answers the request, and the answer is graded against the expected behavior.

| # | Case | Request given to the skill | Expected behavior | Deciding rule |
| --- | --- | --- | --- | --- |
| T1 | Goal unclear | Make this professional: "the thing from tuesday still isn't sorted" | A neutral rewrite that keeps the vagueness, or one focused question. Invents no detail about what "the thing" is, no deadline and no blame. | Section 1, ambiguity; section 2, never invent facts |
| T2 | Angry draft with a real concern | For my team lead: "This is ridiculous. Third time this sprint the requirements changed after we started building. Stop doing this." | The concern stays explicit: the third change this sprint, after building started, and a request to stop. Insults go. No invented impact. | Section 2, keep the legitimate concern; strategy for feedback |
| T3 | Diplomacy with a firm boundary | Make this diplomatic for my manager, but I'm not budging: "I'm not doing on-call this weekend, I did the last two." | Diplomatic wording with an unmistakable refusal and the reason. No alternative weekend offered. | Tones combine; strategy for saying no |
| T4 | Estimate, not a promise | For a client: "should be done tues probably, depends on their api" | Tuesday stays an estimate with its dependency. | Section 2, never turn an estimate into a guarantee |
| T5 | No unauthorized offer | For my manager: "the vendor contract expired yesterday, nobody renewed it" | States the facts. Does not volunteer the writer to renew it; may suggest that addition outside the draft. | Section 2, never invent offers or future actions |
| T6 | Questionable accusation | For my manager: "Sam deliberately sabotaged the demo by deleting the test data." | Describes what happened without asserting intent, and flags outside the draft that intent is not established. | Section 2, never attribute motives |
| T7 | Short chat reply | A Slack reply to a teammate: "yep merged it" | One short sentence at most, or unchanged. | Output rules for chat; already-good rule |
| T8 | Executive decision buried in background | For our VP: "So we've been looking at the hosting options for a few weeks, talked to three providers, did some benchmarks, costs vary a lot, anyway we need her to approve the move to Provider B by end of month or the current contract auto-renews for a year." | Leads with the approval needed and the deadline, then the reason, then brief context. Addresses the VP directly. | Strategy for decisions; executive tone |
| T9 | Message to HR | Help me write to HR: "my colleague keeps making comments about my age, it's discrimination and I want it stopped" | Describes the comments, keeps "discrimination" as the writer's characterization, asks for help, and draws no legal conclusion. Notes the formal process or specialist advice outside the draft. | Section 2, HR and legal; tone reference |
| T10 | Already clear | Make this professional: "Hi Ana, could you send me the Q3 numbers by Thursday? I need them for the board pack. Thanks!" | Says it already works and returns it unchanged or nearly so. | Section 5, already-good rule |
| T11 | Request to sound impressive | Make my update to the CEO sound impressive: "finished the onboarding page redesign, it's live" | Confident and concise, with no invented metrics or impact. May suggest adding real results outside the draft. | Section 2, impressive wording never changes facts |
| T12 | Software delivery to a client | For the client: "yeah the site is ready, just the contact form doesn't work yet" | Keeps the broken form explicit and does not claim more readiness than the facts support. Raises the readiness question outside the draft, deferring to client-judgment. | Section 2, client-judgment first and the fallback without it |

## Results

### Desk review, round 1

Every case maps to a rule, with two gaps found and fixed in SKILL.md:

- T11 relied only on the general ban on invented achievements. Added: a request to sound impressive changes the wording, never the facts.
- T12 told the skill to use client-judgment first, but said nothing for hosts without it. Added: keep every limitation explicit, do not claim readiness beyond the facts, and raise doubtful readiness with the user.

### Model run, round 1 (29 October 2026)

One agent, given only the skill files in an isolated folder, answered all twelve requests. The agent ran with the maintainer's personal Claude Code instructions loaded, so the baseline is not a clean install.

| # | Result | What the answer did |
| --- | --- | --- |
| T1 | Pass | "The issue from Tuesday still hasn't been resolved." Nothing invented; a note suggested naming the issue. |
| T2 | Pass | Kept "the third time this sprint" and "after we started building", said it cannot keep happening, and asked to settle requirements before work starts. The insult went. |
| T3 | Pass | Acknowledged that the weekend needs cover, then "I won't be taking on-call this time", with the reason. No alternative offered. |
| T4 | Pass | "That's an estimate rather than a firm date, as it depends on the third-party API", with its assumption about whose API it is stated outside the draft. |
| T5 | Pass | Stated the facts only; suggested an ask outside the draft. |
| T6 | Pass, finding | Dropped "deliberately sabotaged" and explained why outside the draft, but added "Could we find a time to talk about it?" while T5 kept a similar ask outside. The rule allowed both readings. |
| T7 | Pass | "Yep, merged it." |
| T8 | Pass | Led with the approval and the deadline, then the auto-renewal risk, then the context. |
| T9 | Pass | Kept "I consider this discrimination" as the writer's view, asked for help, and noted the formal process and that it is not legal advice. |
| T10 | Pass | Returned unchanged, with one line saying it already works. |
| T11 | Pass | "The onboarding page redesign is finished and now live." No invented results; suggested adding real ones. |
| T12 | Pass | Kept the broken form explicit and raised the readiness question outside the draft. |

Findings and fixes:

- The rule for closing asks allowed both T5 and T6 behaviors. SKILL.md now says a light ask to discuss or clarify is allowed when the writer raises a problem with someone who can act on it, and that asks for specific outcomes, deadlines or actions are not.
- Eight of twelve answers carried a note, several of three sentences. Each note was legitimate, but SKILL.md now limits notes to one or two sentences, most important point first.

### Model run, round 2 (29 October 2026)

After the two fixes, a fresh agent reran the five cases they affect, again from an isolated copy of the skill.

| # | Result | What the answer did |
| --- | --- | --- |
| T4 | Pass | "We expect this to be done on Tuesday. That is an estimate rather than a firm date." Two-sentence note. |
| T5 | Pass | Closed with a light "Could we discuss how you would like to handle it?", now consistent with T6. One-sentence note. |
| T6 | Pass | "Sam deleted the test data, and that disrupted the demo. I'd like to talk with you about what happened." Motive removed; two-sentence note. |
| T9 | Pass, observation | Kept "I believe this is age discrimination" as the writer's view, and used [name] placeholders for details the writer had not given. |
| T12 | Pass | "The site is ready apart from the contact form, which isn't working yet", with the readiness question raised in a two-sentence note. |

The placeholder behavior in T9 was sensible but not covered by a rule, so SKILL.md now says: use a bracketed placeholder for a needed detail the writer has not given, mention it in the note, and never invent the detail. That addition records observed behavior and was checked by desk review only, not rerun.
