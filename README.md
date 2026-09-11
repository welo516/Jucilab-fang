# JUCILab Writing Skill

`jucilab-writing` is a Codex skill for polishing and auditing computer-science and technical academic manuscripts. It emphasizes field-common wording, reviewer-defensible logic, cautious claims, and concise revision notes.

It also embeds a distilled advisor review model: diagnosis rules and repair patterns are distilled from real advisor annotations on group manuscripts (evolutionary computation, data mining, NAS, causal learning, and Bayesian network structure learning), so the skill can act as a Fang/JUCILab advisor-style reviewer as well as a manuscript polisher.

## What It Does

- **Advisor-style diagnosis**: checks motivation, section identity, figure-method alignment, terminology consistency, contribution visibility, and evidence-chain breaks before any sentence polishing.
- **Field-common rewriting**: final manuscript text uses wording that is common in the target subfield and published papers, with cautious and bounded claims.
- **Repair patterns**: version-to-version evolution patterns from past revised drafts help choose how to repair similar issues.
- **Word-level audit**: collocations, compound terms, pronouns, sentence length, punctuation discipline, and consistency checks.

## Repository Structure

```text
SKILL.md                        # Skill entry: task routing, hard constraints, claim hygiene, language-only mode, output conventions
references/review.md            # Substantive review toolbox: advisor diagnosis, severity, section tasks, claim tightening, fact table, version-chain repair patterns
references/domain-causal-bnsl.md # Domain pack: causal / DAG / BNSL claim boundaries, terms, method and experiment checks
references/examples.md          # Case library distilled from advisor annotations, plus a worked abstract rewrite
references/corpus.md            # Advisor annotation corpus (single source of truth; loaded only for corpus/rule maintenance)
references/corpus.json          # Structured corpus
agents/openai.yaml              # Interface metadata
```

The repository root is the skill folder. After installation, `SKILL.md` should be located directly at:

```text
~/.codex/skills/jucilab-writing/SKILL.md
```

## Install on macOS

Clone the repository directly into the Codex skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/welo516/Jucilab-Writing.git ~/.codex/skills/jucilab-writing
```

If the folder already exists, update it instead:

```bash
cd ~/.codex/skills/jucilab-writing
git pull
```

If `CODEX_HOME` is configured, install to:

```bash
$CODEX_HOME/skills/jucilab-writing
```

## Install on Windows

Open PowerShell and run:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills" | Out-Null
git clone https://github.com/welo516/Jucilab-Writing.git "$env:USERPROFILE\.codex\skills\jucilab-writing"
```

If the folder already exists, update it instead:

```powershell
cd "$env:USERPROFILE\.codex\skills\jucilab-writing"
git pull
```

If `CODEX_HOME` is configured, install to:

```powershell
$env:CODEX_HOME\skills\jucilab-writing
```

## Use

Restart Codex or open a new Codex thread after installation. Use prompts such as:

```text
Use $jucilab-writing to polish this abstract and check field-common wording, logic, and reviewer risks.
```

## Update

Because the skill is installed as a Git repository, updates can be pulled directly:

```bash
cd ~/.codex/skills/jucilab-writing
git pull
```

On Windows PowerShell:

```powershell
cd "$env:USERPROFILE\.codex\skills\jucilab-writing"
git pull
```

## Contribute

Contributions can be submitted through pull requests. Keep changes focused on manuscript-polishing behavior, field-common wording checks, reviewer-risk diagnosis, and output-format rules.

## License

This project is licensed under the [Apache License 2.0](LICENSE).
