---
name: file-distillation
description: Use when the user asks to 提炼, 蒸馏, distill, condense, refine, or extract reusable knowledge from a local document into an Obsidian/CareerOS knowledge base.
---

# File Distillation

## Overview

Turn a source document into a concise Markdown career-asset note, place it in the best matching folder under `E:\Obsidian-works-here\Personal-Assets\CareerOS`, and preserve the CareerOS inflow model:

```text
weekly signal or source document
-> distilled note
-> evidence-ready asset
-> STAR interview case
-> public-safe portfolio narrative
```

Stop for user confirmation whenever the source appears unclear, possibly wrong, unsafe to publish, or ambiguous in target asset type.

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

4. Inspect the CareerOS structure and operating pages.
   - Read directory names and nearby Markdown note titles under `E:\Obsidian-works-here\Personal-Assets\CareerOS`.
   - Read `CareerOS\README.md`, `CareerOS\00_Dashboard\Home.md`, and `CareerOS\00_Dashboard\Asset_Pipeline.md` if present.
   - Use the existing folder taxonomy and naming style. Prefer the closest existing directory over creating a new one.
   - Create a new subdirectory only when no existing directory reasonably fits; explain why before doing so unless the user already instructed it.
   - Treat `CareerOS\10_Public_Portfolio` as the external expression layer. Write there only when the output is fully public-safe.

5. Classify the output before writing.
   - Choose exactly one primary `asset_type`: `project`, `architecture`, `methodology`, `brag`, `interview`, `strategy`, or `public_portfolio`.
   - Choose one `maturity`: `raw`, `distilled`, `evidence-ready`, `star-ready`, or `public-ready`.
   - Choose one `confidentiality`: `private`, `sanitized`, or `public`.
   - Do not assume `distilled` means `public`. A distilled note can still be private or sanitized.
   - If the source contains internal terms, private metrics, internal links, screenshots, raw data, company code, customer/person identifiers, or proprietary implementation details, the output must not be `confidentiality: public` unless those details are removed or generalized.

6. Distill the note.
   - Keep the durable knowledge, decisions, frameworks, definitions, reusable procedures, and source-specific insights.
   - Remove filler, repeated phrasing, chatty transitions, raw brainstorming noise, and one-off execution details.
   - Preserve useful links, citations, commands, examples, and code snippets when they support future reuse.
   - Use clear Markdown headings and concise bullets. Prefer Chinese output if the source or user request is Chinese; otherwise match the source language.
   - Add a short "来源" or "Source" line pointing to the original document path.
   - If evidence is missing, write `result needs evidence` rather than inventing metrics.
   - For project assets, include role, constraints, contribution, decisions, results, public-safe expression, and next asset step.
   - For interview assets, include Situation, Task, Action, Result, follow-up details, and sanitization checks.
   - For public portfolio assets, keep only public-safe content and use generalized business or technical context.

7. Write the distilled Markdown file.
   - Save it inside the selected CareerOS directory.
   - Choose a filename that matches local naming conventions and avoids collisions. If a file exists, create a timestamped or disambiguated filename rather than overwriting.
   - Add frontmatter using the CareerOS metadata model.
   - After writing, report the output path, selected directory rationale, classification, suggested index update, suggested `Asset_Pipeline.md` update, and any unresolved assumptions.

8. Keep the operating surfaces current when it is safe and obvious.
   - Add or suggest a row in the relevant folder index.
   - Add or suggest a row in `CareerOS\00_Dashboard\Asset_Pipeline.md` for the asset's current maturity and next step.
   - If the asset supports target-role positioning, add or suggest a row in `CareerOS\07_Career_Strategy\Capability_Evidence_Matrix.md`.
   - If the right row content is ambiguous, stop and ask instead of guessing.

9. Keep CareerOS local-only.
   - Work in `E:\Obsidian-works-here\Personal-Assets`.
   - Never run `git fetch`, `git pull`, `git rebase`, or `git push` for `Personal-Assets` or any `CareerOS` content.
   - Never add or restore a Git remote for `Personal-Assets` as part of distillation work.
   - Do not sync, publish, upload, mirror, or otherwise send `CareerOS` content to a remote repository.
   - Leave distilled changes in the local working tree unless the user explicitly asks for a local-only commit.
   - If the user asks to sync, push, publish, or reconnect remote tracking for `CareerOS` or `Personal-Assets`, stop and explain that CareerOS is intentionally local-only.

## Confirmation Gate

Ask the user before continuing when any of these appear:

- Content may be wrong or misleading.
- Meaning depends on missing context.
- The best target CareerOS directory is ambiguous.
- A new directory seems necessary.
- Distillation would require deleting nuance that may be important.
- The output could be public-facing but public safety is uncertain.
- The asset type, maturity level, confidentiality level, target roles, or capabilities are ambiguous.

When asking, quote or summarize only the smallest relevant excerpt and give the concrete decision needed. Continue only after the user answers.

## Output Shape

A typical distilled note should use this structure when it fits the content:

```markdown
---
source: "<original path>"
distilled: true
created: YYYY-MM-DD
updated: YYYY-MM-DD
asset_type: project | architecture | methodology | brag | interview | strategy | public_portfolio
maturity: raw | distilled | evidence-ready | star-ready | public-ready
confidentiality: private | sanitized | public
target_roles:
  - "<role name>"
capabilities:
  - "<capability name>"
tags:
  - asset/<type>
  - maturity/<level>
  - confidentiality/<level>
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
- Marking a note public just because it is distilled.
- Writing to `10_Public_Portfolio` without enforcing the public-safety rules.
- Omitting CareerOS frontmatter, which makes future pipeline tracking harder.
- Running `git fetch`, `git pull`, `git rebase`, or `git push` for `Personal-Assets` or `CareerOS`.
- Re-adding a Git remote to `Personal-Assets` during distillation work.
- Treating local-only CareerOS notes as safe to sync because they are already distilled.
- Staging unrelated `.obsidian` or vault changes while committing a distilled asset.
