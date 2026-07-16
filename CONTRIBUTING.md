# Contributing to Gate Skills

Thank you for your interest in contributing! This repository curates and maintains Claude Code (and multi-platform) skills for frontend/Next.js development.

## How to Contribute

### Adding a New Skill

1. **Fork** this repository
2. **Create** a skill directory under the appropriate category:
   ```
   skills/
     your-skill-name/
       SKILL.md      # Required: skill definition
       references/   # Optional: supporting docs
   ```
3. **Write** your `SKILL.md` following the standard format:
   - **Description**: What the skill does, when to trigger it
   - **Instructions**: Step-by-step guidance
   - **Triggers**: Keywords/phrases that activate the skill
4. **Test** your skill locally:
   ```bash
   node bin/install.js --skill your-skill-name
   ```
5. **Submit** a PR with:
   - Your skill directory
   - Updated entry in the Skills Registry (README.md)
   - Brief description of what the skill does

### Skill Quality Standards

- **Trigger clarity**: Triggers must be unambiguous and specific
- **No hallucination**: Instructions must be grounded in real patterns
- **Concise**: Keep SKILL.md under 500 lines
- **Tested**: Verify the skill works with Claude Code before submitting
- **Platform notes**: If skill is platform-specific, note it in the description

### Skills Registry Format

Add your skill to the README.md table:

```markdown
| [Skill Name](skills/your-skill/) | Trigger keywords | Description | Platform |
```

### Reporting Issues

- Use GitHub Issues for bug reports
- Include: skill name, expected vs actual behavior, Claude Code version

### License

By contributing, you agree that your contributions will be licensed under the same license as this project.
