# Latex-in-codespaces
Repository model for LaTeX editing via GitHub Codespaces.

## Overview
A GitHub Codespaces-ready repository for LaTeX authoring enables seamless editing, compilation, and preview of documents directly in the browser or VS Code. It leverages devcontainer configurations for instant setup with TeX Live, LaTeX Workshop extension, and automated builds. This model suits teams or executives managing technical reports, theses, or publications requiring version control and collaboration.

## Core Structure
Organize files as follows for optimal Codespaces integration:

```text
latex-repo/
├── .devcontainer/
│   ├── devcontainer.json      # Defines TeX environment and VS Code extensions
│   └── Dockerfile             # Customized image
├── .github/
│   └── workflows/             # CI/CD for PDF builds on push/PR
│       └── latex.yml
├── src/my-project/            # LaTeX source files
│   ├── main.tex               # Primary document
│   ├── chapters/              # Modular chapters
│   └── assets/                # Images, bib files
└── README.md                  # Setup instructions
```

## Getting Started

### How to compile the LaTeX document
/workspaces/Latex-in-codespaces/src/my-project/interactnlmsample.tex
```bash
cd "/workspaces/Latex-in-codespaces/src/my-project" && pdflatex -interaction=nonstopmode interactnlmsample.tex
```

### How to compile with bibliography

```bash
# 1. Compile the .tex file with pdflatex (first pass)
pdflatex interactnlmsample.tex

# 2. Process the references with bibtex
bibtex interactnlmsample

# 3. Compile again with pdflatex (second pass)
pdflatex interactnlmsample.tex

# 4. Compile a third time to resolve cross-references
pdflatex interactnlmsample.tex
```

### How to clean strange characters preventing compilation

```bash
find src/my-project/ -name '*.tex' -print0 | xargs -0 perl -CS -pi -e 's/\x{200B}//g'
```

Codespaces supports real-time collaboration without local installs. Enjoy it.