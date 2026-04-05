# How to Decide What to Create

Detect the current repository state first. Do not assume any repo type in advance.

## Step 1: Classify the repository

Read the file tree, package manifests, configs, and source code. Determine project type from evidence. Do not force a classification — describe what you observe.

## Step 2: Identify what exists now

From files you read, determine: what distinct areas of responsibility exist, which warrant their own skills, and which are too small to justify dedicated files.

## Step 3: Scale `.claude/` to the repo

**Minimal/blank repo:** Lean `CLAUDE.md` + minimal `context.md`. One skill (task-execution). No skills for nonexistent concerns.

**Growing repo:** When new responsibilities emerge (verified by new files/patterns), create skills then. Update `context.md`.

**Mature repo:** Skills for every distinct concern. Commands for recurring team workflows.

## The golden rule

Create only what the repo justifies now. When something new appears — verified by evidence — create it then.
