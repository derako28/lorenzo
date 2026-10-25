---
name: "reply-slop-check"
description: "Anti-AI-slop pass for @lorenzofl0w reply comments (15-40 words): warm-up replies under Business & Finance accounts and follow-ups under own posts. Run on every drafted reply before posting. Catches AI tells in short-form replies, enforces human voice, and offers a question variant. Trigger on \"slop check reply\", \"check reply\", \"проверь реплай\"."
---

# Skill: Reply Anti-Slop Check (@lorenzofl0w)

Перенесено 25.10.2026 из скилла другого аккаунта и подогнано под Lorenzo. Правила ответов аккаунта —
раздел «Ответы и прогрев» в `brief.md`; он важнее этого файла. Механика меток за ответы —
`x-algorithm.md` (SpamHighRecall за спам-ответы под чужими постами, сентябрь 2026).

## Why this exists
X's slop classifier (`BangerInitialScreenGemmaClassifier`) flags replies too. Accumulated slop labels the ACCOUNT `llm_slop_user` (adds `SpamHighRecall`, 30-day TTL). Replies are SHORT (15-40 words, 1-3 sentences), so a single AI tell can contaminate the entire text. The density matters more than in a 300-word post. Every reply must pass.

## Reply format options (6 types)
When drafting reply variants, always offer at least one from the first five, and include a **Type 6 (Question)** variant when the user requests it or when the post invites debate.

1. **Concrete number/fact** — drop a specific figure, date, or data point the post didn't mention
2. **Counterexample** — name one case that complicates or contradicts the post's claim
3. **Specific experience/story** — a concrete detail that reads as first-hand knowledge
4. **Source expansion** — name the paper, book, chapter, or filing that extends the post's point
5. **Sharp question** — one question that reframes the post or exposes a gap
6. **Question** — a genuine, open-ended question that invites the author to think further. NOT rhetorical. NOT "have you considered..." (that is AI). A question a peer at a bar would actually ask. Examples:
   - "What does the failure rate look like past year ten?"
   - "Does this hold when rates are above 5%?"
   - "Where does the 40 cents figure come from in the original Graham, Security Analysis or The Intelligent Investor?"
   - "How many of those funds survived the full 20-year SPIVA window versus closed and got dropped from the data?"

   Question rules:
   - One question only. Never two questions in one reply.
   - No setup sentence before the question. Just ask it.
   - No "Great point, but..." or "This raises an interesting question:" — AI throat-clearing.
   - The question must be specific enough that it has a real answer, not philosophical.
   - Avoid "Have you considered..." / "Isn't it worth noting..." / "Don't you think..." — these are AI patterns masquerading as questions.

## Kill-list — AI tells in short replies (remove or rewrite)

### Tier 1: instant flag (kill on sight in a 30-word reply)
- **Compliment opener**: "Great point", "This is spot on", "Excellent observation", "Well said", "So true" — NEVER start a reply this way
- **"It's worth noting that..."** / "It's important to remember..." / "It should be noted..." — hedging filler, screams LLM
- **"This is a great example of..."** — meta-commentary instead of content
- **"Indeed"** / "Furthermore" / "Moreover" / "Notably" / "Essentially" / "Fundamentally" — formal register that no human uses in a tweet reply
- **"The key takeaway here is..."** / "What's interesting here is..." — AI framing instead of just saying the thing
- **"This reminds me of..."** — bridge phrase; just say what it reminds you of
- **"Couldn't agree more"** / "Absolutely" as a standalone opener — empty agreement

### Tier 2: suspicious in density (one is okay, two in 30 words = rewrite)
- **Symmetric antithesis**: "It was not X. It was Y." — once per reply MAX, and only if the contrast is concrete. Two in one reply = rewrite.
- **Tidy parallel structure**: three clauses of equal length in a row. Break the rhythm.
- **Hollow closer**: a profound-sounding last line that states nothing checkable. Cut it or replace with a fact.
- **Perfect grammar in casual context**: every sentence grammatically flawless, every comma correct, no contractions. Add a contraction, drop an article, use a fragment.
- **Over-explaining**: saying in 35 words what could be said in 20. If you can cut 10 words and lose nothing, do it.
- **Agreeing before disagreeing**: "You're right, but..." / "Fair point, however..." — just say the disagreement.
- **Passive voice**: "It can be argued that..." — say who argues it.
- **Bookend structure**: opening and closing with the same word/phrase for rhetorical effect. In 30 words this screams craft.

### Tier 3: context-dependent (check against the rest)
- **Em dashes**: banned (account voice rule). Recast the sentence, or use a spaced hyphen « - ».
- **Colon-heavy**: "Here is the thing:" / "The answer:" — plain sentences instead.
- **Emoji**: banned unless quoting (account voice rule).
- **Exclamation marks**: never in a reply. Lorenzo does not exclaim.
- **Stacked numbers**: more than one figure in a reply. Keep the one that carries the point.

### Friendly is not a compliment opener
`brief.md` wants replies to acknowledge what works in the post and add to it, not correct the author.
Do it with content, not praise: pick up the post's own detail and continue it ("The IRS didn't forget,
though."). "Great point" / "Love this" stay banned.

## Must-have — what makes a reply read as human expert

1. **Jumps straight to content** — no throat-clearing, no compliment, no "here's the thing". First word is part of the point.
2. **One specific detail** — a name, a number, a year, a filing, a chapter. Something only someone who has read the source would know.
3. **Uneven rhythm** — a short fragment next to a longer sentence, or vice versa. Perfectly balanced = AI.
4. **Flat or dry tone** — no excitement, no hype, no "this is huge". Expert peers don't exclaim at each other.
5. **Trusts the reader** — states a fact without explaining why it matters. The reader gets it.
6. **Can end flat** — not every reply needs a mic-drop closer. Sometimes the fact IS the closer.

## Three hard tests (all must pass)

### 1. The bar test
Read the reply out loud. Would a finance person at a bar actually say this sentence to someone, unprompted, after hearing their point? If it sounds like a LinkedIn comment, rewrite.

### 2. The density test
In a 30-word reply, every word matters. Can you cut 5+ words and keep the meaning? If yes, cut them. Target: no filler words, no warm-up, no padding.

### 3. The twin test
Put the reply next to 5 real human replies on finance X. Does it blend in or stand out as "too polished"? A reply that is noticeably better-written than everything around it is suspicious. Aim for peer-level, not professor-level.

## Process
1. Draft 2-3 reply variants per the 6 types above.
2. Run each variant through the kill-list: scan for every Tier 1 item (instant kill), then Tier 2 (count — two items = rewrite), then Tier 3.
3. Run the three hard tests on each surviving variant.
4. If a variant needs more than two fixes, rewrite from scratch. Patching AI voice does not work; it just produces polished AI voice.
5. Present clean variants with type label and word count, and a Russian translation under each English variant (`RU:` in italics).
6. When the user asks for a question ("вопрос", "question", "добавь вопрос"), always include a Type 6 variant.
7. Every fact in a reply gets «проверить: <источник>», same as in posts.

## Quick reference — human reply patterns to imitate
- "The IRS didn't forget, though. After she died, they filed a claim against her estate for millions." (own reply under the Aretha Franklin post, 15.10.2026: 19.7K views, 100 likes — continues the story with a new twist)
- "He began paying for advice years after Epstein's guilty plea. Whether the tax plan worked doesn't answer why he chose that adviser." (Polina's example of a simple reply: plain sentences, one point)
- "The 4% rule was tested on 30-year windows. He retired at 30." (flat, factual, lets the gap speak)
- "He sold a year later for 50% and called it his worst decision." (story beat, dry)

