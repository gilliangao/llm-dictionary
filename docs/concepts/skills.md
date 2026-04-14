Skills

In LLM systems, a skill is a reusable package of instructions that helps the model do a specific job better

In normal words
    A skill is like a mini guide for one task
    It tells the model what this skill is for and how to use it
    Example: GitHub review skill, SQL skill, PDF skill, or writing skill

Basic structure
    skill-name/
    ├── SKILL.md
    ├── agents/
    ├── scripts/
    ├── references/
    └── assets/

Main file
    SKILL.md is the core file
    It usually has metadata at the top and instructions below

Metadata
    Metadata is small information about the skill
    It helps the system know when to use the skill
    Common fields:
        name: skill name
        description: what the skill does and when to use it

Example metadata
    ---
    name: github
    description: Use for GitHub repo, PR, and issue tasks
    ---

Why metadata matters
    The model may see the metadata before reading the full skill
    Good metadata makes it easier to select the right skill
    Bad metadata can cause the wrong skill to be used

Body of the skill
    Below the metadata is the instruction text
    This explains the workflow, rules, tools, and best practices

Optional folders
    agents/ = UI metadata for showing the skill in lists or chips
    scripts/ = helper code for repeatable tasks
    references/ = extra docs loaded only when needed
    assets/ = templates, images, or files used by the skill

How to use it in an LLM
    The system first checks the metadata to decide if the skill matches the task
    If it matches, it reads the skill instructions
    Then the model follows that guidance while answering or doing work
