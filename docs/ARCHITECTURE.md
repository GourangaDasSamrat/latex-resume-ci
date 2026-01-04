# Architecture Overview

This document describes the architecture and workflow of the
**latex-resume-ci** automation pipeline.

---

## 🎯 Goal

To provide a fully automated, reproducible CI/CD pipeline for compiling
LaTeX resumes into PDFs with zero manual intervention.

---

## 🧱 High-Level Components

```

┌────────────┐
│   Developer│
│ edits .tex │
└─────┬──────┘
│ git push
▼
┌─────────────────────┐
│ GitHub Actions CI   │
│ (ubuntu-latest)    │
└─────┬──────────────┘
│
▼
┌─────────────────────┐
│ Dockerized LaTeX    │
│ (texlive-full)     │
└─────┬──────────────┘
│
▼
┌─────────────────────┐
│ Compiled PDFs       │
│ + GitHub Release    │
└─────────────────────┘

```

---

## ⚙️ Workflow Steps

1. **Trigger**
   - On push to `main`
   - Or manual `workflow_dispatch`

2. **Resume Discovery**
   - Automatically detects directories containing `main.tex`

3. **Compilation**
   - Uses a Docker container (`texlive-full`)
   - Runs `latexmk` for reproducible PDF builds

4. **Artifact Handling**
   - Generated PDFs are:
     - Uploaded as workflow artifacts
     - Committed back to the repository

5. **Release Automation**
   - A new GitHub Release is created automatically
   - PDFs are attached to the release

6. **Documentation Automation**
   - README.md is dynamically generated
   - Includes download badges, release links, and build metadata

---

## 🧠 Design Principles

- **Automation-first**: No manual steps after pushing code
- **Reproducibility**: Docker ensures consistent builds
- **Scalability**: Supports multiple resume variants
- **Clean History**: Atomic commits and CI-skipping where appropriate
- **Transparency**: Auto-generated documentation

---

## 📁 Repository Structure

```

/
├── <variant>/        # Resume variants (each with main.tex)
├── common/           # Shared LaTeX components
├── .github/workflows # CI/CD configuration
├── README.md         # Auto-generated documentation
├── ARCHITECTURE.md   # This file
├── SECURITY.md
└── LICENSE

```

---

## 🚀 Future Improvements

- Docker layer caching for faster builds
- Semantic versioned releases
- Workflow visualization diagrams
- Optional PDF validation checks
