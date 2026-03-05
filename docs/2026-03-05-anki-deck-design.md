# Anki Flashcard Deck Design -- Claude Code Wiki

**Date:** 2026-03-05
**Purpose:** Memorization tool for workshop delivery of Claude Code training to development and product teams

## Problem

65 wiki articles across 7 sections. Content was researched and written over time but specific details (numbers, thresholds, config keys, decision frameworks) have faded. Need to internalize this material well enough to deliver live workshops, field questions on the fly, and look like the subject matter expert in the room.

## Approach

Anki spaced repetition deck generated from wiki content, paired with teach-back exercise prompts. Targets four learning modes: flashcard drilling, teaching/explaining, building/doing (config completion), and visual/spatial (mental model construction through scenario work).

## Card Types

### 1. Factual Recall

Straight Q&A on specifics that matter in a workshop setting. Numbers, thresholds, config keys, pricing, limits.

Example:

- Front: _What triggers automatic context compaction?_
- Back: _~75-92% context window usage_

### 2. Scenario Cards

Workshop attendee describes a problem, you diagnose it. Builds the "fielding questions" muscle.

Example:

- Front: _A PM says Claude "forgot" everything they discussed 20 minutes ago. What happened and what do you tell them?_
- Back: _Context compaction triggered. Older messages were summarized to free space. Explain that Claude has a fixed context window (~200K tokens), compaction preserves recent turns but summarizes older ones. Recommend: use /compact proactively, keep critical info in CLAUDE.md files, use subagents for research-heavy work._

### 3. Config/Command Completion

Partial config or command, fill in the blank. Cloze deletion format where Anki supports it.

Example:

- Front: _To use Bedrock as the API provider, set `___=1`_
- Back: _CLAUDE_CODE_USE_BEDROCK_

### 4. Teach-Back Prompts

Topic to explain out loud in 60 seconds. Back of card lists key points as self-check, not a script.

Example:

- Front: _Explain why subagents save context window space._
- Back: Key points to hit:
  - Subagents get isolated context windows (separate from parent)
  - Research results summarized back to parent -- only the answer crosses the boundary
  - 97.5% context savings on delegated work
  - Trade-off: subagent can't see parent's full conversation history

## Sub-deck Structure

Parent deck: `Claude Code Wiki`

| Sub-deck           | Source section                                                                                                                                                                                                        | Card emphasis                                                                 |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Internals          | system-prompt, context-management, prompt-caching, token-optimization, extended-thinking, tool-execution-context                                                                                                      | Heavy factual recall -- numbers, thresholds, mechanics                        |
| Guides             | effective-prompting, workflow-patterns, debugging-techniques, testing-strategies, model-selection, memory-organization, permissions-enterprise, coding-assistants-context, essential-plugins, spec-driven-development | Mix of scenario cards and config completion                                   |
| Extending          | extension-mechanisms, custom-extensions, hooks-cookbook, integration-patterns, agent-teams                                                                                                                            | Config completion and scenario cards                                          |
| Enterprise Rollout | All articles across phases 0-3 + appendix (25 articles)                                                                                                                                                               | Scenario-heavy -- client questions, architecture decisions, pushback handling |
| Product            | product-thinking, prioritization-tradeoffs, requirements-specifications, user-research, prototyping-iteration                                                                                                         | Teach-back prompts -- conversation topics                                     |
| Training Paths     | developer-path, platform-engineer-path, product-manager-path                                                                                                                                                          | Teach-back prompts -- curriculum structure rationale                          |

Estimated total: 300-400 cards.

## Card Quality Filter

Not every sentence becomes a card. The filter: _"Would I look bad if someone asked me this in a workshop and I blanked?"_ If yes, it's a card. Background detail nobody would quiz you on gets skipped.

## Card Rules

- One fact per card -- never compound questions
- Scenario cards use realistic setups ("A developer on your team says..."), not abstract framing
- Config cards use cloze deletion where possible
- Teach-back prompts list 3-4 key points on back as self-check
- Every card tagged with `section::topic` (e.g., `internals::prompt-caching`, `enterprise::phase-0`)

## Output Format

Anki tab-separated `.txt` files, one per sub-deck. Each line: `front\tback\ttag1 tag2`. Files stored outside the wiki repo (personal study materials, not wiki content).

Output directory: `~/Documents/anki-claude-code/`

## Generation Process

1. Subagents read each article and extract card-worthy material
2. Cards written following the rules above
3. Tagged by section and topic
4. Output as importable `.txt` files
5. Manual review pass to cut unnecessary cards before import

## Study Schedule (4 weeks)

### Week 1: Internals + Guides

- Import Internals and Guides sub-decks
- 20 new cards/day, review all due cards daily
- End of week: one teach-back prompt per day, timed to 60 seconds

### Week 2: Add Extending + Enterprise Rollout

- Import remaining technical sub-decks
- 15 new cards/day (review queue growing)
- Focus on enterprise scenario and pushback-handling cards

### Week 3: Add Product + Training Paths, full shuffle

- All sub-decks active, shuffled review across everything
- 10 new cards/day, clear the review backlog
- 2-3 teach-back prompts daily, random topic selection

### Week 4: Simulated workshop prep

- Zero new cards. Pure review and teach-back practice.
- Pick a section, set 5-minute timer, explain it cold
- Flag hesitation cards as weak spots to hammer

### Daily Time

15-20 minutes card review + 5-10 minutes teach-back practice. Under 30 minutes total.
