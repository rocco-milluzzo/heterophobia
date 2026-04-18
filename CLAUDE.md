# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Italian dystopian sci-fi novel called "HETEROPHOBIA" (Tales from Aeternitas: Volume I). Set in 2105 Ex-Europa, where immortality has made reproduction obsolete and heterosexuality is banned by law.

## File Structure

- `capitoli/` - 41 chapter files in markdown (00-prefazione.md through 40-nota-autore.md), continuous numbering
- `HETEROPHOBIA.md` - Concatenated full novel (regenerated from chapters)
- `HETEROPHOBIA.pdf` - Print-ready PDF
- `INDICE.md` - Table of contents pointing to chapter files
- `personaggi.md` - Character sheets with family trees
- `worldbuilding.md` - Timeline (2023-2105), technology, geography
- `outline.md` - Chapter-by-chapter synopsis
- `illustrazioni.md` - AI prompt descriptions for cover and chapter illustrations
- `quarta-di-copertina.md` - Back cover copy
- `lettera-editore.md` - Cover letter for publishers
- `book-style.css` - CSS for PDF generation

## Commands

### Regenerate full manuscript and PDF
```bash
# Concatenate all chapters
echo '# HETEROPHOBIA\n\n*Tales from Aeternitas: Volume I*\n\n---\n\nUn romanzo di Rocco Milluzzo\n\n---\n' > HETEROPHOBIA.md && for f in capitoli/*.md; do cat "$f" >> HETEROPHOBIA.md && echo -e "\n\n" >> HETEROPHOBIA.md; done

# Generate PDF via weasyprint
pandoc HETEROPHOBIA.md -o HETEROPHOBIA.html --standalone --toc --toc-depth=1 --metadata title="HETEROPHOBIA" --css=book-style.css && weasyprint HETEROPHOBIA.html HETEROPHOBIA.pdf
```

## Key Characters

- **James Valeri** - Male protagonist, archivist
- **Kate Ferrante** - Female protagonist, biologist
- **Alice Valeri Ferrante** - Their illegal daughter, secret narrator
- **Marta** - Kate's grandmother, mother of Elena
- **Elena** - Kate's mother (deported 2083)
- **Enrico Ferrante** - Kate's father (signed dissociation papers)
- **Enzio** - James's grandfather, archivist

## Narrative Structure

The story is told by a mysterious narrator (revealed as Alice at the end) who reconstructs her parents' love story through documents, recordings, and memories. Chapters alternate between:
- Present-day investigation (Alice's voice)
- Flashbacks of James and Kate
- "Frammento" chapters (testimonies from Marta, Enzio, Enrico)

## Writing Guidelines

- Language: Italian
- Tone: Intimate over ideological, never didactic
- No emojis unless explicitly requested
- When editing, preserve exact indentation and formatting
- Chapter titles follow pattern: "# Capitolo N: Title" (italiano)
- **Avoid AI writing artifacts**: never use em-dash "—" or en-dash "–" as punctuation (replace with comma, colon, parenthesis, or full stop). No exceptions.
- Avoid tricolo patterns "X. Y. Z." when not motivated; avoid aphorisms in dialogue; avoid isolated one-word lines used for "impact".
- Check Italian accents carefully: perché, però, né, sé, lì, là, dà, è.
- Keep virgolette dritte `" "` in source markdown (the PDF renderer converts them); apostrofi ASCII `'` are acceptable in source.
- Chronology anchors: James and Kate born 2080, meet 2095, first night 2098, propose child 2103, Alice conceived 2105, Alice born 2106, raid and separation 2122, Alice narrates from 2132.
