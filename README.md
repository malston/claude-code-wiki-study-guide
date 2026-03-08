# Claude Code Wiki Study Guide

Anki spaced repetition flashcards generated from the [Claude Code Wiki](https://malston.github.io/claude-code-wiki/). Designed for workshop delivery prep -- memorizing the specifics you need to teach Claude Code to development and product teams without fumbling for details.

## Install Anki

```bash
brew install --cask anki
```

## Import the Decks

1. Open Anki
2. Go to **File > Import**
3. Select a `.txt` file from `decks/`
4. Set the field separator to **Tab**
5. Map the fields: Field 1 = Front, Field 2 = Short, Field 3 = Long, Field 4 = Tags
6. Set the note type to **Short/Long Answer** (create it first if it doesn't exist -- see Card Types below)
7. Set the deck name using the `Claude Code Wiki::` prefix (e.g., `Claude Code Wiki::Internals`)
8. Click **Import**
9. Repeat for each file

## Decks

| File                     | Cards | Focus                                                       |
| ------------------------ | ----- | ----------------------------------------------------------- |
| `internals.txt`          | 78    | Numbers, thresholds, pricing, mechanics -- the foundation   |
| `guides.txt`             | 93    | Workflow scenarios, config completion, practical how-to     |
| `extending.txt`          | 68    | Hooks, MCP, agent teams -- config-heavy                     |
| `enterprise-rollout.txt` | 107   | Client scenarios, architecture decisions, pushback handling |
| `product.txt`            | 49    | Teach-back prompts for PM workflows and frameworks          |
| `training-paths.txt`     | 32    | Curriculum design rationale and structure                   |

**427 cards total.**

## Card Types

- **Factual Recall** -- Q&A on specific numbers, thresholds, config keys
- **Scenario Cards** -- "A developer says..." or "A CISO asks..." -- you diagnose or respond
- **Config/Command Completion** -- fill in the blank on commands, env vars, settings
- **Teach-Back Prompts** -- explain a topic in 60 seconds, key points on the back for self-check

## Study Schedule (4 weeks)

### Week 1: Internals + Guides

- Import those two sub-decks
- 20 new cards/day, review all due cards daily
- End of week: one teach-back prompt per day out loud, timed to 60 seconds

### Week 2: Add Extending + Enterprise Rollout

- Import remaining technical sub-decks
- 15 new cards/day (review queue growing)
- Focus on enterprise scenario and pushback-handling cards

### Week 3: Add Product + Training Paths

- All sub-decks active, shuffled review across everything
- 10 new cards/day, clear the review backlog
- 2-3 teach-back prompts daily, random topic selection

### Week 4: Simulated workshop prep

- Zero new cards -- pure review and teach-back practice
- Pick a section, set a 5-minute timer, explain it cold
- Flag any card where you hesitate -- those are your weak spots

### Daily time: ~30 minutes

15-20 minutes card review + 5-10 minutes teach-back practice.

## Tags

Every card is tagged with `section::topic` for filtered review. Examples:

- `internals::prompt-caching`
- `guides::permissions`
- `enterprise::pushback`
- `product::prioritization`
- `training::pm-path`

Use Anki's **Custom Study > Limit to certain tags** to drill a specific topic before a workshop on that subject.

## Regenerating Cards

These cards were generated from the wiki content by Claude Code using parallel agents (one per section). To regenerate after wiki updates, see the design doc in the wiki repo at `docs/plans/2026-03-05-anki-deck-design.md`.
