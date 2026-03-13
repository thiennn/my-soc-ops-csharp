# Soc Ops

> **Social Bingo for in-person mixers.** Roam the room, find people who match the squares, get 5 in a row — first to shout *Bingo!* wins.

[![Play Now](https://img.shields.io/badge/▶_Play_Now-live_demo-4ade80?style=for-the-badge)](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/)
[![Lab Guide](https://img.shields.io/badge/📚_Lab_Guide-read_online-60a5fa?style=for-the-badge)](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/)
[![.NET 10](https://img.shields.io/badge/.NET-10-512bd4?style=for-the-badge&logo=dotnet)](https://dotnet.microsoft.com/download/dotnet/10.0)
[![Blazor WASM](https://img.shields.io/badge/Blazor-WebAssembly-7c3aed?style=for-the-badge)](https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor)

---

## What Is This?

Soc Ops turns a room full of strangers into a game show. Each player gets a **5×5 bingo board** filled with icebreaker prompts — *"Has visited more than 3 countries"*, *"Can name a design pattern"*, *"Owns a pet fish"*. You mingle, find real people who match, mark the square, and race to five in a row.

This repo is also the codebase for a **hands-on GitHub Copilot Agent Lab** — a guided workshop that teaches you to build features using custom agents, prompt files, and context engineering.

---

## The Stack

| Layer | Tech |
|---|---|
| Framework | Blazor WebAssembly (.NET 10) |
| Styling | Custom utility CSS (`app.css`) — no Bootstrap |
| State | `BingoGameService` + `localStorage` persistence |
| Logic | Static `BingoLogicService` — board gen, toggle, win detection |
| Deploy | GitHub Pages (auto on push to `main`) |

---

## Quick Start

```bash
git clone https://github.com/thiennn/my-soc-ops-csharp
cd my-soc-ops-csharp
dotnet run --project SocOps/SocOps.csproj
# → http://localhost:5166
```

**Prerequisites:** [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) or higher.

---

## Workshop Lab Guide

A step-by-step lab that walks you from a blank game to a fully multi-agent-built feature — using only GitHub Copilot in VS Code.

| Step | What You'll Build |
|------|-------------------|
| [**00 · Overview**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=00-overview) | Goals, checklist, and project orientation |
| [**01 · Setup**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=01-setup) | Context engineering with instruction files |
| [**02 · Design**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=02-design) | Design-first frontend with a custom skill |
| [**03 · Quiz Master**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=03-quiz-master) | Custom agent that generates question sets |
| [**04 · Multi-Agent**](https://dotnet-presentations.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=04-multi-agent) | Orchestrating multiple agents together |

> Prefer offline? All guides live in [`workshop/`](workshop/).

---

## Contributing

Found a bug or want to add questions to the bank? Open an issue or PR — see [CONTRIBUTING.md](CONTRIBUTING.md).
