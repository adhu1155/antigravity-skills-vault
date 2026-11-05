# 🌌 Antigravity Skills Vault

A curated collection of custom skills for the [Antigravity](https://antigravity.google) AI coding assistant and agentic workflows.

---

## 📂 Repository Structure

Skills in this vault follow the standard Antigravity skill structure:

```text
antigravity-skills-vault/
├── skills/
│   └── <skill-name>/
│       ├── SKILL.md          # Skill definition (YAML frontmatter + markdown instructions)
│       ├── scripts/          # Optional helper scripts and utilities
│       ├── resources/        # Optional templates and assets
│       └── references/       # Optional reference docs and specs
├── README.md
└── LICENSE
```

---

## 🛠️ Installation & Usage

### Option 1: Workspace Scope
To use a skill in a specific project/workspace, copy the skill folder to `.agent/skills/` (or `.agents/skills/`) inside your project:

```bash
mkdir -p /path/to/project/.agent/skills
cp -r skills/<skill-name> /path/to/project/.agent/skills/
```

### Option 2: Global Scope (CLI)
To make a skill available globally across all projects using `antigravity-cli`:

```bash
mkdir -p ~/.gemini/antigravity-cli/skills
cp -r skills/<skill-name> ~/.gemini/antigravity-cli/skills/
```

### Option 3: Global Scope (Antigravity IDE / App)
For the Antigravity IDE:

```bash
mkdir -p ~/.gemini/config/skills
cp -r skills/<skill-name> ~/.gemini/config/skills/
```

---

## 📋 Available Skills

| Skill | Description | Directory |
| :--- | :--- | :--- |
| [`ats-checker`](./skills/ats-checker/) | Evaluates a candidate's LaTeX CV against a job description and produces a transparent ATS-alignment report. | [`skills/ats-checker/`](./skills/ats-checker/) |
| [`cold-mail`](./skills/cold-mail/) | Creates personalized, professional job-search cold emails tailored to companies and key decision makers. | [`skills/cold-mail/`](./skills/cold-mail/) |
| [`cover-letter`](./skills/cover-letter/) | Writes tailored, evidence-based cover letters highlighting relevant experience for specific roles. | [`skills/cover-letter/`](./skills/cover-letter/) |
| [`cv-tailor`](./skills/cv-tailor/) | Customizes the candidate's LaTeX CV for a specific job, saving outputs to a dedicated `Tailored/` folder. | [`skills/cv-tailor/`](./skills/cv-tailor/) |
| [`job-finder`](./skills/job-finder/) | Discovers and verifies open job listings tailored to the candidate's skills, saving structured reports. | [`skills/job-finder/`](./skills/job-finder/) |
| [`job-application-tracker`](./skills/job-application-tracker/) | Central job application tracking management with master CSV database, follow-ups, and analytics. | [`skills/job-application-tracker/`](./skills/job-application-tracker/) |

---

## ✍️ Creating a New Skill

Each skill requires at minimum a `SKILL.md` with YAML frontmatter:

```markdown
---
name: your-skill-name
description: A concise description of what this skill does and when the agent should use it.
---

# Your Skill Title

## When to Use This Skill
- Scenario 1...
- Scenario 2...

## Instructions
1. Step-by-step guidance for the agent...
```

---

## 📄 License

[MIT](LICENSE)
