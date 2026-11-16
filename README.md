# SquadLoop local setup

This guide covers installing and starting the SquadLoop agent team in this
repository. It does not start the React frontend or Spring Boot backend.

## Prerequisites

- Node.js 20 or newer, with npm.
- Pi Coding Agent:
  ```bash
  npm install -g @earendil-works/pi-coding-agent
  ```
- tmux 3.2 or newer:
  ```bash
  # macOS
  brew install tmux

  # Ubuntu/Debian
  sudo apt install tmux
  ```
- A Google Gemini API key, available locally as `GEMINI_API_KEY`:
  ```bash
  export GEMINI_API_KEY="your-api-key"
  ```
  Set the key in your local environment; do not add it to this repository or
  commit it.

## Install SquadLoop locally

Git clone outside of demo project
```
git clone git@github.com:balajirags/squadloop.git
```

```bash
cd squadloop
npm install -g squadloop
npm link
```

## Initialize in Target Repository

From the repository root, initialize the local SquadLoop configuration once:

```bash
cd demo-squadloop
```

```bash
squadloop init
```

## Configuration and workflows

After initialization, inspect the local `.squadloop/` directory:

- `config.json` contains the SquadLoop configuration.
- `workflows/` contains the available workflow definitions.

These files are local-only and Git-ignored, so they are available in your
initialized checkout but are not included in repository clones.

Then check the installation and start the team using tmux:

```bash
squadloop doctor
squadloop start --ex-mode=team --driver=tmux
```

To attach to an active session from another terminal:

```bash
squadloop attach
```

`squadloop init` creates local configuration under `.squadloop/`. Run it only
for a fresh local setup; do not rerun it to repair an existing configuration.
Before starting the agent team, review your working tree because agents may
modify project files.
