# Deep Research Skill

**Free Perplexity/Gemini-level deep research for Claude Code, Cursor, Copilot, and any agent-skills compatible tool.**

Research any topic with 20-40+ sources, get structured reports with footnotes, then generate podcasts, videos, slides, and quizzes from your findings — all from one command.

---

## Why This Exists

Deep research tools like Perplexity Pro, Gemini Deep Research, and ChatGPT Deep Research cost $20/month and lock you into their platforms. This skill gives you the same capabilities for free, running inside your existing AI coding agent.

**And it does things they can't:**

| Feature | Perplexity Pro | Gemini Deep | ChatGPT Deep | **This Skill** |
|---------|:-:|:-:|:-:|:-:|
| Internet research | Yes | Yes | Yes | **Yes** |
| Deep iterative mode | Pro only | Pro only | Plus only | **Free** |
| Your local files | No | Google Drive | Upload | **NotebookLM** |
| Domain boost | No | No | No | **Yes** |
| Research to podcast | No | Manual | No | **Automatic** |
| Research to video | No | No | No | **Yes** |
| Research to slides | No | No | No | **Yes** |
| Research to quiz | No | No | No | **Yes** |
| Continue/resume | No | No | No | **Yes** |
| Compare mode | No | No | No | **Yes** |
| Source credibility | No | No | No | **Yes** |
| Cross-agent compatible | No | No | No | **Yes** |
| **Cost** | $20/mo | $20/mo | $20/mo | **Free** |

## Quick Install

### Claude Code
```bash
# Copy to your skills directory
mkdir -p ~/.claude/skills/deep-research
curl -o ~/.claude/skills/deep-research/SKILL.md \
  https://raw.githubusercontent.com/athanasopoulosc/deep-research-skill/main/SKILL.md
```

### Other Agents (Cursor, Copilot, Codex)
Copy `SKILL.md` to your agent's skills directory. The skill follows the [agent-skills](https://agentskills.io) open standard.

## Optional: Full Power Mode

Install NotebookLM for deep research + artifact generation:

```bash
pip install notebooklm-py
notebooklm login
```

Without NotebookLM, the skill falls back to WebSearch-only mode (still works, but no podcast/video/slides/quiz generation).

## Usage

### Basic Research
```
/deep-research "ballast water treatment regulations 2026"
```

### With Domain Boost
```
/deep-research --domain maritime "enclosed space entry procedures"
/deep-research --domain academic "transformer architecture improvements"
/deep-research --domain legal "GDPR compliance requirements 2026"
```

### Compare Two Topics
```
/deep-research --compare "React vs Svelte for enterprise apps"
```

### Continue Previous Research
```
/deep-research --continue
```

## How It Works

```
User query
    |
    v
[Pre-flight] --> You choose depth (1-5) + source focus
    |
    v
[NotebookLM Deep Research] --> Gemini searches 20+ sources
    |
    v
[Domain Boost] --> Targeted searches (IMO, SOLAS, arXiv, etc.)
    |
    v
[Synthesis] --> Structured report with footnotes + credibility tags
    |
    v
[Post-Research Menu]
    |
    +---> Save as .md
    +---> Generate podcast
    +---> Generate video
    +---> Generate slide deck
    +---> Generate quiz/flashcards
    +---> Ask follow-up questions
    +---> Go deeper on a section
    +---> Compare with another topic
```

### Depth Levels

| Depth | Mode | Sources | Time |
|:-----:|------|:-------:|:----:|
| 1 | Quick | 5-10 | ~1 min |
| 2 | Moderate | 10-15 | ~2 min |
| **3** | **Standard** | **20+** | **~3 min** |
| 4 | Deep | 30+ | ~5 min |
| 5 | Exhaustive | 40+ | ~8 min |

### Domain Boost

When you specify `--domain`, the skill adds targeted searches to authoritative sources:

- **Maritime**: IMO, SOLAS, STCW, ISM Code, IACS, class societies (DNV, Lloyd's, BV, ABS)
- **Legal**: Legislation databases, official journals, court decisions, regulatory frameworks
- **Academic**: Google Scholar, arXiv, PubMed, IEEE, ResearchGate, peer-reviewed journals

### Report Format

Reports follow the Gemini Deep Research style:

```markdown
# Topic -- Deep Research Report

**Generated:** 2026-03-29 | **Sources:** 24 | **Depth:** Standard | **Domain:** Maritime

## Executive Summary
Key findings in 3-5 sentences.

## 1. First Major Theme
Analysis with footnotes.^1,2

## Key Findings
- Finding 1 -- actionable takeaway
- Finding 2 -- practical implication

## Contradictions & Open Questions
- Where sources disagree

---
### Sources
^1 Title -- URL -- [official]
^2 Title -- URL -- [academic]
```

Each source gets a credibility tag: `[official]`, `[academic]`, `[industry]`, `[news]`, or `[blog]`.

### Post-Research Actions

After the report, you can:
- **[S]** Save as .md file
- **[P]** Generate podcast from findings
- **[V]** Generate video explainer
- **[D]** Generate slide deck (.pptx)
- **[Q]** Generate quiz or flashcards
- **[F]** Ask follow-up questions
- **[+]** Go deeper on a specific section
- **[C]** Compare with another topic

## Requirements

**Minimum (fallback mode):**
- Any agent supporting the [agent-skills](https://agentskills.io) standard
- WebSearch + WebFetch tools (built-in to most agents)

**Recommended (full mode):**
- [notebooklm-py](https://github.com/teng-lin/notebooklm-py) (`pip install notebooklm-py`)
- Google account for NotebookLM authentication

## Architecture

This is a single-file skill (`SKILL.md`) with no external dependencies. It uses:

1. **NotebookLM's Gemini-powered research engine** for deep web research (20+ sources per query)
2. **WebSearch + WebFetch** for domain-specific targeted searches and fallback mode
3. **NotebookLM artifact generation** for podcast, video, slides, quiz output
4. **Source credibility scoring** to tag each source by authority level

The skill follows the [agent-skills](https://agentskills.io) open standard and works with Claude Code, Cursor, GitHub Copilot, Gemini CLI, OpenAI Codex, and any compatible agent.

## Contributing

Contributions welcome! Areas to improve:

- **New domains**: Add domain boost configs for medical, engineering, finance, etc.
- **Report templates**: Alternative report formats beyond Gemini-style
- **Language support**: Localized pre-flight prompts and report headers
- **Testing**: Document edge cases and error scenarios

## License

MIT -- see [LICENSE](LICENSE)

---

Built by [Christos Athanasopoulos](https://github.com/athanasopoulosc)
