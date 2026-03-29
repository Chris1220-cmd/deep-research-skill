# Contributing to Deep Research Skill

Thanks for your interest in improving the deep research skill!

## How to Contribute

### Adding a New Domain

1. Fork this repository
2. Open `SKILL.md`
3. Add a new subsection under **Domain Boost**:

```markdown
### Medical (`--domain medical`)

Additional search queries:
- `"{topic}" site:pubmed.ncbi.nlm.nih.gov`
- `"{topic}" clinical trial results`
- `"{topic}" systematic review`
- `"{topic}" site:who.int`
- `"{topic}" medical guidelines`

Source priority:
1. Peer-reviewed medical journals (Lancet, NEJM, BMJ)
2. WHO/CDC guidelines
3. Clinical trial databases
4. Medical society publications
5. Health news outlets
```

4. Update the `argument-hint` in the frontmatter to include the new domain
5. Submit a PR

### Improving the Skill

- Keep changes to `SKILL.md` focused and well-documented
- Test with at least one real query before submitting
- Describe what you changed and why in the PR description

### Reporting Issues

- Open an issue describing the problem
- Include the query you used, the depth/focus settings, and what went wrong
- Note whether you were using Full mode (NotebookLM) or Fallback mode (WebSearch only)

## Code of Conduct

Be respectful, constructive, and collaborative. We're all here to make research better.
