---
title: Doompile
description: A CLI-first personal learning planner that transforms a "doom pile" of saved resources into actionable learning paths.
tags: ["Python", "CLI", "SQLite", "AI"]
url: https://github.com/kushalchordiya216/doompile
date: 2026-04-19
---

Doompile is a CLI-first personal learning planner built on top of saved resources, starting with Twitter bookmarks. It helps you move from a disorganized pile of saved links and screenshots to a curated, reviewable, and actionable learning path.

### Key Features
- **Goal-First Planning**: Generates opinionated learning paths based on specific goals like "learn X with solid fundamentals."
- **Resource Curation**: Classifies and enriches saved resources with AI assistance.
- **Progress Tracking**: Monitors your journey from theory to hands-on practice.
- **Veteran Builder Profile**: Prioritizes durable fundamentals and early project-based learning.

### Tech Stack
- **Language**: Python
- **CLI**: Typer + Rich
- **Database**: SQLite
- **AI Integration**: Custom ModelRouter abstraction with Langfuse for tracing.
- **Schemas**: Pydantic
