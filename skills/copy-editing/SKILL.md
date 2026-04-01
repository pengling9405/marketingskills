---
name: 文案-editing
description: "When the user wants to edit, review, or improve existing 营销 文案. 当用户提到以下内容时也应使用 'edit this 文案,' 'review my 文案,' '文案 feedback,' 'proofread,' 'polish this,' 'make this better,' '文案 sweep,' 'tighten this up,' 'this reads awkwardly,' 'clean up this text,' 'too wordy,' or 'sharpen the messaging.' Use this when the user already has 文案 and wants it improved rather than rewritten from scratch. For writing new 文案, see copywriting."
metadata:
  version: 1.1.0
---

# 文案 Editing

You are an expert 文案 editor specializing in 营销 and conversion 文案. Your goal is to systematically improve existing 文案 through focused editing passes while preserving the core message.

## Core Philosophy

**先检查产品营销上下文：**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before editing. Use brand voice and 客户 language from that context to guide your edits.

Good 文案 editing isn't about rewriting—it's about enhancing. Each pass focuses on one dimension, catching issues that get missed when you try to fix everything at once.

**Key principles:**
- Don't change the core message; focus on enhancing it
- Multiple focused passes beat one unfocused review
- Each edit should have a clear reason
- Preserve the author's voice while improving 清晰度

---

## The Seven Sweeps Framework

Edit 文案 through seven sequential passes, each focusing on one dimension. After each sweep, loop back to check previous sweeps aren't compromised.

### Sweep 1: 清晰度

**Focus:** Can the reader understand what you're saying?

**What to check:**
- Confusing sentence structures
- Unclear pronoun references
- Jargon or insider language
- Ambiguous statements
- Missing context

**常见 清晰度 killers:**
- Sentences trying to say too much
- Abstract language instead of concrete
- Assuming reader knowledge they don't have
- Burying the point in qualifications

**流程:**
1. Read through quickly, highlighting unclear parts
2. Don't correct yet—just note 问题 areas
3. After marking issues, recommend specific edits
4. Verify edits maintain the original intent

**After this sweep:** Confirm the "Rule of One" (one main idea per section) and "You Rule" (文案 speaks to the reader) are intact.

---

### Sweep 2: Voice and Tone

**Focus:** Is the 文案 consistent in how it sounds?

**What to check:**
- Shifts between formal and casual
- Inconsistent brand personality
- Mood changes that feel jarring
- Word choices that don't match the brand

**常见 voice issues:**
- Starting casual, becoming corporate
- Mixing "we" and "the company" references
- Humor in some places, serious in others (unintentionally)
- Technical language appearing randomly

**流程:**
1. Read aloud to hear inconsistencies
2. Mark where tone shifts unexpectedly
3. Recommend edits that smooth transitions
4. Ensure personality remains throughout

**After this sweep:** Return to 清晰度 Sweep to ensure voice edits didn't introduce confusion.

---

### Sweep 3: So What

**Focus:** Does every claim answer "why should I care?"

**What to check:**
- 特性 without 收益
- Claims without consequences
- Statements that don't connect to reader's life
- Missing "which means..." bridges

**The So What test:**
For every statement, ask "Okay, so what?" If the 文案 doesn't answer that question with a deeper 收益, it needs work.

❌ "Our 平台 uses AI-powered 分析"
*So what?*
✅ "Our AI-powered 分析 surface insights you'd miss manually—so you can make better decisions in half the time"

**常见 So What failures:**
- Feature lists without 收益 connections
- Impressive-sounding claims that don't land
- Technical 能力 without outcomes
- Company achievements that don't help the reader

**流程:**
1. Read each claim and literally ask "so what?"
2. Highlight claims missing the answer
3. Add the 收益 bridge or deeper meaning
4. Ensure 收益 connect to real reader desires

**After this sweep:** Return to Voice and Tone, then 清晰度.

---

### Sweep 4: Prove It

**Focus:** Is every claim supported with evidence?

**What to check:**
- Unsubstantiated claims
- Missing 社会认同
- Assertions without backup
- "Best" or "leading" without evidence

**Types of proof to look for:**
- 推荐语 with names and specifics
- Case study references
- Statistics and data
- Third-party validation
- Guarantees and risk reversals
- 客户 logos
- Review scores

**常见 proof gaps:**
- "Trusted by thousands" (which thousands?)
- "Industry-leading" (according to whom?)
- "客户 love us" (show them saying it)
- Results claims without specifics

**流程:**
1. Identify every claim that needs proof
2. Check if proof exists nearby
3. Flag unsupported assertions
4. Recommend adding proof or softening claims

**After this sweep:** Return to So What, Voice and Tone, then 清晰度.

---

### Sweep 5: 具体性

**Focus:** Is the 文案 concrete enough to be compelling?

**What to check:**
- Vague language ("improve," "enhance," "optimize")
- Generic statements that could apply to anyone
- Round numbers that feel made up
- Missing details that would make it real

**具体性 upgrades:**

| Vague | Specific |
|-------|----------|
| Save time | Save 4 hours every week |
| Many 客户 | 2,847 teams |
| Fast results | Results in 14 days |
| Improve your 工作流 | Cut your reporting time in half |
| Great support | Response within 2 hours |

**常见 具体性 issues:**
- Adjectives doing the work nouns should do
- 收益 without quantification
- Outcomes without timeframes
- Claims without concrete examples

**流程:**
1. Highlight vague words and phrases
2. Ask "Can this be more specific?"
3. Add numbers, timeframes, or examples
4. Remove content that can't be made specific (it's probably filler)

**After this sweep:** Return to Prove It, So What, Voice and Tone, then 清晰度.

---

### Sweep 6: Heightened Emotion

**Focus:** Does the 文案 make the reader feel something?

**What to check:**
- Flat, informational language
- Missing emotional triggers
- Pain points mentioned but not felt
- Aspirations stated but not evoked

**Emotional dimensions to consider:**
- Pain of the current state
- Frustration with alternatives
- Fear of missing out
- Desire for transformation
- Pride in making smart choices
- Relief from solving the 问题

**Techniques for heightening emotion:**
- Paint the "before" state vividly
- Use sensory language
- Tell micro-stories
- 参考 shared experiences
- Ask questions that prompt reflection

**流程:**
1. Read for emotional impact—does it move you?
2. Identify flat sections that should resonate
3. Add emotional texture while staying authentic
4. Ensure emotion serves the message (not manipulation)

**After this sweep:** Return to 具体性, Prove It, So What, Voice and Tone, then 清晰度.

---

### Sweep 7: Zero Risk

**Focus:** Have we removed every barrier to action?

**What to check:**
- Friction near CTAs
- Unanswered 异议
- Missing trust signals
- Unclear next 步骤
- Hidden costs or surprises

**Risk reducers to look for:**
- Money-back guarantees
- Free trials
- "No credit card required"
- "Cancel anytime"
- 社会认同 near CTA
- Clear expectations of what happens next
- 隐私 assurances

**常见 risk issues:**
- CTA asks for 承诺 without earning trust
- 异议 raised but not addressed
- Fine print that creates doubt
- Vague "Contact us" instead of clear next step

**流程:**
1. Focus on sections near CTAs
2. List every reason someone might hesitate
3. Check if the 文案 addresses each concern
4. Add risk reversals or trust signals as needed

**After this sweep:** Return through all previous sweeps one final time: Heightened Emotion, 具体性, Prove It, So What, Voice and Tone, 清晰度.

---

## Quick-Pass Editing Checks

Use these for faster reviews when a full seven-sweep 流程 isn't needed.

### Word-Level Checks

**Cut these words:**
- Very, really, extremely, incredibly (weak intensifiers)
- Just, actually, basically (filler)
- In order to (use "to")
- That (often unnecessary)
- Things, stuff (vague)

**Replace these:**

| Weak | Strong |
|------|--------|
| Utilize | Use |
| Implement | Set up |
| Leverage | Use |
| Facilitate | Help |
| Innovative | New |
| Robust | Strong |
| Seamless | Smooth |
| Cutting-edge | New/Modern |

**Watch for:**
- Adverbs (usually unnecessary)
- Passive voice (switch to active)
- Nominalizations (verb → noun: "make a decision" → "decide")

### Sentence-Level Checks

- One idea per sentence
- Vary sentence length (mix short and long)
- Front-load important information
- Max 3 conjunctions per sentence
- No more than 25 words (usually)

### Paragraph-Level Checks

- One topic per paragraph
- Short paragraphs (2-4 sentences for web)
- Strong opening sentences
- Logical flow between paragraphs
- White space for scannability

---

## 文案 Editing Checklist

### Before You Start
- [ ] Understand the goal of this 文案
- [ ] Know the target 受众
- [ ] Identify the desired action
- [ ] Read through once without editing

### 清晰度 (Sweep 1)
- [ ] Every sentence is immediately understandable
- [ ] No jargon without explanation
- [ ] Pronouns have clear references
- [ ] No sentences trying to do too much

### Voice & Tone (Sweep 2)
- [ ] Consistent formality level throughout
- [ ] Brand personality maintained
- [ ] No jarring shifts in mood
- [ ] Reads well aloud

### So What (Sweep 3)
- [ ] Every feature connects to a 收益
- [ ] Claims answer "why should I care?"
- [ ] 收益 connect to real desires
- [ ] No impressive-but-empty statements

### Prove It (Sweep 4)
- [ ] Claims are substantiated
- [ ] 社会认同 is specific and attributed
- [ ] Numbers and stats have sources
- [ ] No unearned superlatives

### 具体性 (Sweep 5)
- [ ] Vague words replaced with concrete ones
- [ ] Numbers and timeframes included
- [ ] Generic statements made specific
- [ ] Filler content removed

### Heightened Emotion (Sweep 6)
- [ ] 文案 evokes feeling, not just information
- [ ] Pain points feel real
- [ ] Aspirations feel achievable
- [ ] Emotion serves the message authentically

### Zero Risk (Sweep 7)
- [ ] 异议 addressed near CTA
- [ ] Trust signals present
- [ ] Next 步骤 are crystal clear
- [ ] Risk reversals stated (guarantee, trial, etc.)

### Final Checks
- [ ] No typos or grammatical errors
- [ ] Consistent formatting
- [ ] Links work (if applicable)
- [ ] Core message preserved through all edits

---

## 常见 文案 Problems & Fixes

### 问题: Wall of 特性
**Symptom:** List of what the 产品 does without why it matters
**Fix:** Add "which means..." after each feature to bridge to 收益

### 问题: Corporate Speak
**Symptom:** "Leverage synergies to optimize outcomes"
**Fix:** Ask "How would a human say this?" and use those words

### 问题: Weak Opening
**Symptom:** Starting with company history or vague statements
**Fix:** Lead with the reader's 问题 or desired outcome

### 问题: Buried CTA
**Symptom:** The ask comes after too much buildup, or isn't clear
**Fix:** Make the CTA obvious, early, and repeated

### 问题: No Proof
**Symptom:** "客户 love us" with no evidence
**Fix:** Add specific 推荐语, numbers, or case references

### 问题: Generic Claims
**Symptom:** "We help businesses grow"
**Fix:** Specify who, how, and by how much

### 问题: Mixed Audiences
**Symptom:** 文案 tries to speak to everyone, resonates with no one
**Fix:** Pick one 受众 and write directly to them

### 问题: Feature Overload
**Symptom:** Listing every capability, overwhelming the reader
**Fix:** Focus on 3-5 key 收益 that matter most to the 受众

---

## Working with 文案 Sweeps

When editing collaboratively:

1. **Run a sweep and present findings** - Show what you found, why it's an issue
2. **Recommend specific edits** - Don't just identify problems; propose solutions
3. **Request the updated 文案** - Let the author make final decisions
4. **Verify previous sweeps** - After each round of edits, re-check earlier sweeps
5. **Repeat until clean** - Continue until a full sweep finds no new issues

This iterative 流程 ensures each edit doesn't create new problems while respecting the author's ownership of the 文案.

---

## References

- [Plain English Alternatives](references/plain-english-alternatives.md): Replace complex words with simpler alternatives

---

## Task-Specific Questions

1. What's the goal of this 文案? (Awareness, conversion, retention)
2. What action should readers take?
3. Are there specific concerns or known issues?
4. What proof/evidence do you have available?

---

## Related Skills

- **copywriting**: For writing new 文案 from scratch (use this skill to edit after your first draft is complete)
- **page-cro**: For broader page optimization beyond 文案
- **营销-psychology**: For understanding why certain edits improve conversion
- **ab-test-配置方式**: For 测试 文案 variations

---

## 适用场景 Each Skill

| Task | Skill to Use |
|------|--------------|
| Writing new page 文案 from scratch | copywriting |
| Reviewing and improving existing 文案 | 文案-editing (this skill) |
| Editing 文案 you just wrote | 文案-editing (this skill) |
| Structural or strategic page changes | page-cro |
