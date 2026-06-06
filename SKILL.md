---
name: file-distillation
description: Use when the user asks to 提炼, 蒸馏, distill, condense, refine, or extract reusable knowledge from a local document into an Obsidian/CareerOS knowledge base.
---

# File Distillation

## Overview

Turn a source document into a concise Markdown knowledge note, place it in the best matching folder under `E:\Obsidian-works-here\Personal-Assets\CareerOS`, and stop for user confirmation whenever the source appears unclear or possibly wrong.

## Workflow

1. Resolve the source path from the user's message.
   - Accept absolute paths, relative paths from the current workspace, and quoted Obsidian-style file paths.
   - If multiple plausible documents match, ask the user which one to use before reading content.
   - If no document can be found, report the paths checked and ask for a valid path.

2. Read the document completely.
   - Preserve headings, links, code blocks, tables, and frontmatter as context while analyzing.
   - Do not rewrite or overwrite the source document.

3. Check content quality before distilling.
   - Stop and ask for confirmation if a claim appears factually suspicious, internally inconsistent, unsupported by nearby context, garbled, mistranscribed, or logically unclear.
   - Stop if key terms, names, dates, numbers, file references, or causal claims look ambiguous.
   - For current or high-stakes factual claims, verify with reliable sources when appropriate and cite the source in the confirmation question.
   - Do not silently "fix" uncertain claims. Ask concise, concrete questions and wait for the user.

4. Inspect the CareerOS structure.
   - Read directory names and nearby Markdown note titles under `E:\Obsidian-works-here\Personal-Assets\CareerOS`.
   - Use the existing folder taxonomy and naming style. Prefer the closest existing directory over creating a new one.
   - Create a new subdirectory only when no existing directory reasonably fits; explain why before doing so unless the user already instructed it.

5. Distill the note.
   - Keep the durable knowledge, decisions, frameworks, definitions, reusable procedures, and source-specific insights.
   - Remove filler, repeated phrasing, chatty transitions, raw brainstorming noise, and one-off execution details.
   - Preserve useful links, citations, commands, examples, and code snippets when they support future reuse.
   - Use clear Markdown headings and concise bullets. Prefer Chinese output if the source or user request is Chinese; otherwise match the source language.
   - Add a short "来源" or "Source" line pointing to the original document path.

6. Write the distilled Markdown file.
   - Save it inside the selected CareerOS directory.
   - Choose a filename that matches local naming conventions and avoids collisions. If a file exists, create a timestamped or disambiguated filename rather than overwriting.
   - After writing, report the output path, selected directory rationale, and any unresolved assumptions.

## Confirmation Gate

Ask the user before continuing when any of these appear:

- Content may be wrong or misleading.
- Meaning depends on missing context.
- The best target CareerOS directory is ambiguous.
- A new directory seems necessary.
- Distillation would require deleting nuance that may be important.

When asking, quote or summarize only the smallest relevant excerpt and give the concrete decision needed. Continue only after the user answers.

## Output Shape

A typical distilled note should use this structure when it fits the content:

```markdown
---
source: "<original path>"
distilled: true
created: YYYY-MM-DD
---

# <Concise Knowledge Title>

来源：<original path>

## 核心观点

- ...

## 可复用方法

- ...

## 关键细节

- ...
```

Adapt headings to the document. Do not force empty sections.

## Common Mistakes

- Treating "distillation" as a generic summary. The output should be reusable knowledge placed in the knowledge base, not just a shorter abstract.
- Guessing the target folder from the source path alone. Always inspect CareerOS structure first.
- Correcting suspicious claims silently. Stop and ask.
- Overwriting existing notes. Avoid collisions unless the user explicitly requests replacement.
