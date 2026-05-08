---
name: uestcreport
description: Create, compile, maintain, or refactor lightweight UESTC graduate course report templates based on ThesisUESTC. Use when a user wants a UESTC course report PDF in any project without manually copying template files, or when working with `thesis-uestc.cls`, `main.tex`, XeLaTeX course reports, UESTC cover fields, course-report cleanup, continuous chapter headings, or Codex tasks that mention UESTCreport.
---

# UESTCreport

## Workflow

1. For a new course report in another project, run `scripts/create_report.py` from this skill. It copies the bundled template from `assets/template` into the target project and compiles `main.pdf`.
2. For an existing ThesisUESTC project, inspect the repository before editing. Read `main.tex`, `thesis-uestc.cls`, `latexmkrc`, and files referenced by the entrypoint.
3. Keep the template lightweight. Prefer changing `main.tex`; touch `thesis-uestc.cls` only for reusable class behavior such as cover fields, page-breaking, headings, or shared commands.
4. Preserve XeLaTeX compatibility, Chinese typesetting, bibliography commands, labels, `\ref`, `\cite`/`\citing`, figures, tables, equations, and theorem environments unless the user explicitly asks to remove them.
5. Compile with `latexmk -xelatex main.tex` or the local `latexmkrc`. Report any missing TeX packages or fonts clearly.

## Creating a Report in Any Project

Use the bundled script instead of manually copying template files:

```bash
python <skill-root>/scripts/create_report.py
```

- Default target is the current working directory.
- The script copies `main.tex`, `thesis-uestc.cls`, `thesis-uestc.bst`, `latexmkrc`, `reference.bib`, and `pic/logo.pdf`.
- It refuses to overwrite existing files by default. If the user explicitly wants replacement, run with `--force`.
- It compiles automatically with `latexmk -xelatex main.tex` and creates `main.pdf`.
- Use `--output <dir>` for a different target directory.
- Use `--no-compile` when only the source template should be created.
- If compilation fails, keep the generated files and summarize the LaTeX/log error. Do not delete user files.

## Course Report Shape

- Use `\documentclass[course]{thesis-uestc}` when the class supports course mode.
- Keep the cover fields to: course name, report title, student name, student ID, school/major, and completion date.
- Keep the UESTC logo image in the original cover-logo position.
- Make the cover title exactly `课程报告` and `COURSE REPORT`.
- Remove thesis-only front matter from the default entrypoint: originality declaration, Chinese abstract, English abstract, list of figures, list of tables, and nomenclature/glossary.
- Remove thesis-only back matter from the default entrypoint: acknowledgements, degree-period publications/achievements, and translation appendices.
- Keep references through `\thesisbibliography{...}` unless the user asks for another bibliography workflow.

## Chapter Behavior

- Keep `\chapter` available for users who want report-scale top-level divisions.
- In course-report mode, chapters must not force a page break between each other.
- Keep chapter title spacing consistent before and after every chapter heading; do not rely on manual `\vspace` in `main.tex`.
- Prefer `\section` and `\subsection` for most daily course-report content, but do not break existing cross-reference numbering without a clear reason.

## Editing Guidance

- Do not delete source assets such as `pic/logo.pdf`, `.bib` files, or example chapter files just because `main.tex` no longer references them.
- Avoid broad rewrites of the thesis class. Add guarded course-mode logic so existing thesis modes continue to work.
- Keep placeholders realistic and short in `main.tex`; the file should be usable immediately as a report skeleton.
