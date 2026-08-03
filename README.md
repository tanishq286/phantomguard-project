# 🛡️ PhantomGuard

> **Real-time security guardrails against AI-hallucinated package dependencies and slopsquatting attacks.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

---

## 🚨 The Problem

As developers and autonomous agents increasingly rely on LLM coding tools (Claude Code, GitHub Copilot, ChatGPT), a new supply-chain threat has emerged: **AI Package Hallucination & Slopsquatting**.

LLMs routinely generate non-existent library names when drafting code. Threat actors monitor these patterns and pre-emptively register malicious packages matching common hallucinated names on public registries like PyPI and npm. When a developer or agent runs `pip install` or `npm install`, malicious code is pulled directly into the environment.

## ⚡ The Solution

**PhantomGuard** acts as a zero-trust, low-latency safety layer between your development environment and package managers. It verifies package legitimacy, calculates typosquatting distances, and flags phantom dependencies **before** installation occurs.

---

## ✨ Key Features

* **⚡ Sub-10ms Latency Check:** High-speed cached evaluation ensures security checks don't slow down developer workflows or automated agent pipelines.
* **🔍 Multi-Signal Risk Engine:** 
  * Real-time package registry existence verification (PyPI, npm, Cargo).
  * Levenshtein distance analysis to detect typosquatting against popular libraries.
  * Metadata heuristics (repository age, release frequency, author verification).
* **🛡️ Proactive Interception:** Fails safely by intercepting execution *before* dependency download.
* **🔌 Agent & CI/CD Native:** Functions as a lightweight CLI tool, a pre-commit hook, or an automated pipeline check for AI agent frameworks.

---

## 🚀 Quick Start

### Installation

Clone the repository and install dependencies:

```bash
Basic Usage
1. Scan a requirements file
Bash
phantomguard scan requirements.txt
2. Verify an individual package before installing
Bash
phantomguard verify <package-name> --ecosystem pypi
3. Intercept install commands directly
Bash
phantomguard run pip install <package-name>
🛠️ How It Works
   ┌───────────────────────┐
   │ AI Agent / Developer  │
   └───────────┬───────────┘
               │
               ▼
   ┌───────────────────────┐
   │     PhantomGuard      │ ───►  [1] Registry Verification
   │    Security Engine    │ ───►  [2] Typosquatting Distance Check
   └───────────┬───────────┘ ───►  [3] Metadata Heuristics
               │
      ┌────────┴────────┐
      ▼                 ▼
   [ Safe ]        [ Malicious / Phantom ]
      │                 │
      ▼                 ▼
Execute Install    Abort & Alert User
🗺️ Roadmap
[x] Initial CLI architecture and PyPI verification

[x] Levenshtein-based distance checking

[ ] Support for npm, Cargo, and Go modules

[ ] Native integration hooks for Claude Code and AI agent frameworks

[ ] Automated GitHub Action PR scanner

🤝 Contributing
Contributions are welcome! Whether you're reporting bugs, submitting PRs, or improving documentation, please read our contributing guidelines to get started.

Fork the Project

Create your Feature Branch (git checkout -b feature/AmazingFeature)

Commit your Changes (git commit -m 'Add some AmazingFeature')
Here is a clean, professional, and copy-paste-ready README.md tailored specifically for PhantomGuard.

Markdown
# PhantomGuard 🛡️

> **Real-time defense against AI package hallucinations and supply-chain slopsquatting.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/badge/python-3.9%2B-brightgreen)](https://www.python.org/)
[![Security: Shield](https://img.shields.io/badge/security-active-success)](https://github.com/tanishq286/phantomguard-project)

---

## 📌 Overview

As developers rely more on AI coding assistants and autonomous agents, a new attack vector has emerged: **Package Hallucination Hijacking (Slopsquatting)**. AI models frequently suggest non-existent package dependencies, which malicious actors can pre-register on registries like PyPI or npm to execute arbitrary code during installation.

**PhantomGuard** acts as a lightweight, zero-trust safety layer. It intercepts dependency installation commands and inspects project configuration files in real time to catch hallucinated, typosquatted, or malicious packages before they execute on your machine or CI/CD pipeline.

---

## ✨ Key Features

* ⚡ **Sub-10ms Detection Latency**: Built with aggressive local caching and async verification to ensure zero drag on developer workflows.
* 🔍 **Multi-Signal Verification Engine**:
  * **Registry Existence Check**: Verifies real-time availability across PyPI, npm, and more.
  * **Typosquatting Distance**: Uses Levenshtein distance metrics to detect lookalike package names targeting popular libraries.
  * **Metadata & Age Analysis**: Inspects package creation dates, author signals, and release counts to flag brand-new or suspicious uploads.
* 🤖 **AI-Agent Ready**: Pre-built hooks designed for autonomous coding pipelines, pre-commit configurations, and local shell wrappers.
* 🛠️ **Developer-First CLI**: Clean, structured terminal output with actionable risk scores and mitigation suggestions.

---

## 🚀 Quick Start

### Installation

Clone the repository and install dependencies locally:

```bash
git clone https://github.com/tanishq286/phantomguard-project.git
cd phantomguard-project
pip install -e .
Basic Usage
Scan a manifest file:

Bash
phantomguard scan requirements.txt
Scan an npm manifest:

Bash
phantomguard scan package.json
Intercept a single package before installing:

Bash
phantomguard check <package-name>
⚙️ How It Works
Plaintext
[ Package Request ] 
        │
        ▼
┌─────────────────────────────────┐
│   PhantomGuard Security Engine   │
├─────────────────────────────────┤
│ 1. Local Cache Lookup (<1ms)    │
│ 2. Official Registry API Check  │
│ 3. Distance & Typo Detection    │
│ 4. Metadata Risk Scoring        │
└─────────────────────────────────┘
        │
        ├──► [ SAFE ]    ──► Proceed with installation
        └──► [ WARN/BLOCK ] ─► Alert developer/agent of threat
🤝 Contributing
Contributions are welcome! If you'd like to add support for new package registries, improve detection heuristics, or write integrations for AI frameworks:

Fork the repository

Create your feature branch (git checkout -b feature/NewFeature)

Commit your changes (git commit -m 'Add NewFeature')

Push to the branch (git push origin feature/NewFeature)

Open a Pull Request

📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
git clone [https://github.com/tanishq286/phantomguard-project.git](https://github.com/tanishq286/phantomguard-project.git)
cd phantomguard-project
pip install -e .
