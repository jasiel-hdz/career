# Job Applications

Una carpeta por empresa. Todo versionado en Git.

## Per Application

```
10-job-applications/<company>/
├── resume.pdf          # PDF enviado (no commitear si contiene PII sensible — ver nota abajo)
├── cover_letter.md
├── notes.md            # Research, contactos, timeline
└── interview.md        # Prep + notas post-entrevista
```

## Companies

| Company | Folder | Status |
|---------|--------|--------|
| Amazon | [amazon/](./amazon/) | |
| Microsoft | [microsoft/](./microsoft/) | |
| Mercado Libre | [mercadolibre/](./mercadolibre/) | |
| OpenAI | [openai/](./openai/) | |
| Anthropic | [anthropic/](./anthropic/) | |

## Note on resume.pdf

Prefer `resume.pdf` locally or use `resume.pdf` in `.gitignore` if you don't want PDFs in git. Markdown source can live in `03-resume/` and be exported to PDF per application.
