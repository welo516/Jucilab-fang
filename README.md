# JUCILab Fang Skill

`jucilab-fang` is a Codex skill for polishing and auditing computer-science and technical academic manuscripts. It emphasizes field-common wording, reviewer-defensible logic, cautious claims, and concise revision notes.

The repository root is the skill folder. After installation, `SKILL.md` should be located directly at:

```text
~/.codex/skills/jucilab-fang/SKILL.md
```

## Install on macOS

Clone the repository directly into the Codex skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/welo516/Jucilab-fang.git ~/.codex/skills/jucilab-fang
```

If the folder already exists, update it instead:

```bash
cd ~/.codex/skills/jucilab-fang
git pull
```

If `CODEX_HOME` is configured, install to:

```bash
$CODEX_HOME/skills/jucilab-fang
```

## Install on Windows

Open PowerShell and run:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills" | Out-Null
git clone https://github.com/welo516/Jucilab-fang.git "$env:USERPROFILE\.codex\skills\jucilab-fang"
```

If the folder already exists, update it instead:

```powershell
cd "$env:USERPROFILE\.codex\skills\jucilab-fang"
git pull
```

If `CODEX_HOME` is configured, install to:

```powershell
$env:CODEX_HOME\skills\jucilab-fang
```

## Use

Restart Codex or open a new Codex thread after installation. Use prompts such as:

```text
Use $jucilab-fang to polish this abstract and check field-common wording, logic, and reviewer risks.
```

## Update

Because the skill is installed as a Git repository, updates can be pulled directly:

```bash
cd ~/.codex/skills/jucilab-fang
git pull
```

On Windows PowerShell:

```powershell
cd "$env:USERPROFILE\.codex\skills\jucilab-fang"
git pull
```

## Contribute

Contributions can be submitted through pull requests. Keep changes focused on manuscript-polishing behavior, field-common wording checks, reviewer-risk diagnosis, and output-format rules.
