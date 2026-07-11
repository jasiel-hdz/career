# Career Engineering Repository

Single source of truth for an engineering career.

This repository is the **input**. Resumes, LinkedIn, cover letters, interview prep, and portfolio material are **outputs** generated from it.

---

## What problem this solves

Career documents are usually rewritten from memory under time pressure. Details drift, impact gets invented or forgotten, and the same work gets described inconsistently across formats.

This repository preserves engineering knowledge once—business context, decisions, tradeoffs, contributions, and lessons—so future materials never need to be reconstructed from scratch.

---

## What this is (and is not)

**Is:** documentation of engineering work—problems, solutions, architecture, challenges, and ownership.

**Is not:** a resume dump, a tech laundry list, or a task tracker.

Each project document should let a future reader remember the work without relying on memory.

---

## Organization

```
career/
├── README.md              # This file — purpose and navigation
├── PROFILE.md             # Professional profile (high-level)
├── experience/            # Companies and projects
│   ├── sesaj/
│   ├── stratech/
│   ├── ofnos/
│   ├── sonetasot-cms/
│   └── sonetasot-gis/
└── resume/                # Generated / targeting artifacts
    ├── master-resume.md
    ├── backend.md
    ├── fullstack.md
    └── architect.md
```

| Path | Role |
|------|------|
| `PROFILE.md` | Concise professional profile used as a base for outputs |
| `experience/<company>/` | One company folder; `README.md` for company context |
| `experience/<company>/*.md` | One file per major project |
| `resume/` | Resume variants derived from experience docs |

### Project file sections

Each project file uses a fixed shape:

1. Overview  
2. Business Context  
3. Product Overview  
4. Architecture  
5. My Contributions  
6. Engineering Decisions  
7. Technical Challenges  
8. Infrastructure  
9. Technologies  
10. Impact  
11. Lessons Learned  

Keep project docs concise (roughly 100–150 lines). Prefer depth over coverage of every task.

---

## How this repository is maintained

| Role | Responsibility |
|------|----------------|
| **Author (ChatGPT)** | Writes technical and professional content. Source of truth for facts. |
| **Editor (Cursor)** | Creates files, formats Markdown, keeps structure consistent, updates indexes, flags duplication and link opportunities. Does not invent facts or change technical meaning without approval. |
| **Reviewer (you)** | Validates that content matches real experience. |

### Editor rules

- Integrate new documents into the existing structure.
- Update this README and company indexes when paths or docs change.
- Propose improvements; do not silently rewrite technical content.
- Ask clarifying questions only when a section is marked `[TODO]` or `[NEEDS CLARIFICATION]`.
- Do not add folders or templates unless explicitly requested.
- Keep the repository simple.

### Content rules

- Document engineering work, not job descriptions.
- Prefer ownership verbs (Designed, Architected, Implemented, Led…) and always explain **why**.
- Never invent facts, exaggerate impact, or add responsibilities that were not performed.

---

## Outputs

Artifacts under `resume/` (and later LinkedIn, cover letters, interview notes, portfolio) should be **derived** from `PROFILE.md` and `experience/`.

If a claim cannot be traced to an experience document, it does not belong in an output.

---

## Index

### Profile

- [PROFILE.md](PROFILE.md)

### Experience

- [Sesaj](experience/sesaj/README.md) — [Bóveda](experience/sesaj/boveda.md), [Centinela](experience/sesaj/centinela.md), [Architecture](experience/sesaj/architecture.md)
- [Stratech](experience/stratech/README.md) — [BBVA](experience/stratech/bbva.md), [Farmacias](experience/stratech/farmacias.md), [iFit](experience/stratech/ifit.md)
- [Ofnos](experience/ofnos/README.md) — [Platform](experience/ofnos/platform.md), [Architecture](experience/ofnos/architecture.md)
- [Sonetasot CMS](experience/sonetasot-cms/README.md) — [CMS Platform](experience/sonetasot-cms/cms-platform.md)
- [Sonetasot GIS](experience/sonetasot-gis/README.md) — [GIS Platform](experience/sonetasot-gis/gis-platform.md)

### Resumes

- [Master Resume](resume/master-resume.md)
- [Backend](resume/backend.md)
- [Full Stack](resume/fullstack.md)
- [Architect](resume/architect.md)
