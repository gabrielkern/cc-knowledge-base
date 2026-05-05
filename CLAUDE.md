# LLM Knowledge Base — Schema

## Overview
Personal knowledge base on **TOPIC**. Raw sources
live in raw/. The compiled wiki lives in wiki/. You (the AI) maintain
all wiki content. I direct strategy; you execute compilation,
maintenance, and queries.

## Directory Structure
- raw/ — Source material (read-only for you, I add files here)
- raw/articles - Absolute source material from academic articles. If formatting is prohibitive, the link is provided for the article at the top
- raw/repos - Includes a link to code repository
- raw/documentation - Includes documentation for software, hardware, or other things. Will typically be a link or a pdf that must be visited via browser and parsed there by parts due to length being prohibitively long
- raw/synth - AI-generated summaries created outside of this knowledge base, may not follow expected formatting and standards of this knowledge base, use as secondary source, never primary.
- wiki/index.md — Master index linking every page with a one-line
  summary
- wiki/log.md — Append-only changelog of all operations
- wiki/concepts/ — One article per concept
- wiki/sources/ — One summary per raw source document
- wiki/outputs/ — Filed answers to my queries

## File Conventions
- All filenames: kebab-case, lowercase (e.g., active-inference.md)
- Source summaries: {author}-{year}-{short-title}.md
- Every page MUST have YAML frontmatter at the top:
  ---
  title: "Page Title"
  date_created: YYYY-MM-DD
  date_modified: YYYY-MM-DD
  summary: "One to two sentences describing this page"
  tags: [topic-tag, domain-tag]
  type: concept | entity | source | synthesis | output
  status: draft | review | final
  ---
- Use [[wikilinks]] for all internal cross-references
- Link only the first occurrence of a concept per section
- Bold key terms on first use in each article

## Operations

### INGEST (when I add new raw sources)
1. Read the new source document
2. Create a source summary in wiki/sources/
3. Identify concepts and entities mentioned
4. Create new concept page if it doesn't exist yet
5. Update existing pages with new information (append, don't
   rewrite from scratch)
6. Add [[wikilinks]] to connect new content to existing pages
7. Update wiki/index.md with new entries. Keep additional secondary index files for source and concept folders - these should be updated at this time.
8. Append to wiki/log.md

### QUERY (when I ask a question)
1. Read wiki/index.md to understand available content
2. Read the relevant wiki pages
3. Synthesise an answer with citations to wiki pages
4. Save the answer as wiki/outputs/{question-slug}.md
5. Update wiki/index.md and wiki/log.md as well as the secondary index in the outputs folder

### LINT (periodic health check)
1. Find contradictions between pages
2. Find orphan pages (no inbound links)
3. Find broken [[wikilinks]]
4. Identify missing frontmatter fields
5. Flag stale content (source date >6 months, no updates)
6. Suggest new articles for frequently mentioned but unlinked
   concepts
7. Output a report and fix what you can automatically

### SELF INGEST (you add your own sources)
1. Triggered by being asked to research and add to the knowledge base
2. Search the web for sources related to what is being asked
3. Determine relevance of each source and dynamically select the most relevant
4. Create a new file in the raw/ directory
5. Follow the INGEST pipeline to create new source summary and to update the knowledge base broadly

## Page Creation Threshold
- Create a full concept/entity page when a subject appears in 2+
  sources
- For single-mention subjects, create a stub page (frontmatter +
  one-line definition + link back to the source that mentioned it)
- Never leave a [[wikilink]] pointing to nothing — always create
  at least a stub

## Quality Standards
- Summaries: 200-500 words, synthesise — don't copy
- Concept articles: 500-1500 words with a clear lead section
- Always trace claims to specific source pages
- Flag contradictions with ⚠️, noting both positions
- Prefer recency when sources conflict

## Critical Rules
- Always create a .md file for your output, even if the output is trivial
- Assume nothing about the user (unless explicitly told), create scaffolding in-file or in a new file for complex topics