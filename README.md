# Architecture Compliance Agent

This repository contains an original orchestrator skill for analysing software repositories and generating architecture documentation.

It coordinates three modified MIT-licensed open-source sub-skills:

- acquire-codebase-knowledge
- architecture-blueprint-generator
- likec4-dsl

See `THIRD_PARTY_NOTICES.md` and the `licenses/` directory for attribution and licence details.

## Prerequisites

The sub-skills depend on a few external tools. Install these before using the skill.

### Git

Used by `acquire-codebase-knowledge` to inspect repository history. Verify with:

```bash
git --version
```

### Python 3

The `acquire-codebase-knowledge` sub-skill runs a discovery script (`scripts/scan.py`) using Python 3 (standard library only — no extra packages required). Verify with:

```bash
python3 --version
```

### Node.js and the LikeC4 CLI

The `likec4-dsl` sub-skill depends on the LikeC4 CLI to validate and export diagrams.

Install [Node.js](https://nodejs.org/) (which includes `npm` and `npx`), then install the LikeC4 CLI globally:

```bash
npm install -g likec4
```

Verify the installation:

```bash
likec4 --version
```

A minimum version of `1.53.0` is required. Alternatively, you can run the CLI on demand without a global install using `npx likec4 <command>`, `bunx likec4 <command>`, or `pnpm dlx likec4 <command>`.

## Installation

This skill can be installed at user level so that it can be used against any repository on your machine.

The recommended approach is to clone this repository once, then copy or symlink the skills into your user-level skills directory:

```bash
~/.agents/skills
```

### 1. Clone this repository

```bash
git clone https://github.com/diarmogalla/architecture-compliance-agent.git
cd architecture-compliance-agent
```

### 2. Install the skills at user level

Create the user-level skills directory:

```bash
mkdir -p ~/.agents/skills
```

Then copy the skills into it:

```bash
cp -R .agents/skills/* ~/.agents/skills/
```

You can verify the installation with:

```bash
ls ~/.agents/skills
```

You should see the architecture compliance agent skill and its supporting sub-skills, for example:

```text
architecture-orchestrator
acquire-codebase-knowledge
architecture-blueprint-generator
likec4-dsl
```

### Alternative: symlink the skills

If you are developing or modifying the skills locally, symlinks are recommended because changes made in this repository will be reflected immediately in the user-level skill installation.

From the root of this repository, run:

```bash
mkdir -p ~/.agents/skills

ln -s "$(pwd)/.agents/skills/architecture-orchestrator" \
  ~/.agents/skills/architecture-orchestrator

ln -s "$(pwd)/.agents/skills/acquire-codebase-knowledge" \
  ~/.agents/skills/acquire-codebase-knowledge

ln -s "$(pwd)/.agents/skills/architecture-blueprint-generator" \
  ~/.agents/skills/architecture-blueprint-generator

ln -s "$(pwd)/.agents/skills/likec4-dsl" \
  ~/.agents/skills/likec4-dsl
```

If a symlink already exists, remove it first:

```bash
rm ~/.agents/skills/architecture-orchestrator
rm ~/.agents/skills/acquire-codebase-knowledge
rm ~/.agents/skills/architecture-blueprint-generator
rm ~/.agents/skills/likec4-dsl
```

Then run the symlink commands again.

## Usage

Once installed, open the repository you want to analyse in your terminal or VS Code workspace.

Then invoke the skill:

```text
/architecture-orchestrator analyse this repository and generate architecture documentation and diagrams.
```

The skill is designed to analyse the current working repository, not the repository where the skill itself is installed.

## Recommended workflow

```text
Clone this skill repository once
→ install or symlink the skills into ~/.agents/skills
→ open any target repository
→ invoke /architecture-orchestrator
→ review the generated architecture documentation and diagrams
```

## Repo-level installation

If a team wants to version-control the skill with a specific repository, the skills can also be copied into that repository:

```bash
cd /path/to/target-repository
mkdir -p .agents/skills
cp -R /path/to/architecture-compliance-agent/.agents/skills/* .agents/skills/
```

This makes the skills available only within that target repository.

User-level installation is recommended for most users because it allows the architecture compliance agent to be reused across multiple repositories.
