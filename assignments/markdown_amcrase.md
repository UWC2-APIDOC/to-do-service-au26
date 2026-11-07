# Advantages and disadvantages of lightweight markup

## Advantages

- The format has a short learning curve. A few symbols cover most needs, and developers already
  know them.
- Plain text works with Git. Diffs, blame, PR review, and merges behave as they do for code,
  which makes docs as code workable.
- A README stays legible in a terminal or on GitHub without rendering.
- Files are portable. They do not lock you into one editor or vendor, and the same file can feed
  different site generators or converters.
- Fenced code blocks with language tags simplify writing, highlighting, and extracting code
  samples for testing in CI.
- Writers stay on the keyboard instead of using formatting menus, so drafting is fast.
- A large ecosystem of linters, prose checkers, and site generators supports the format.

## Disadvantages

- Dialects differ on tables, task lists, footnotes, and edge cases, so a file can render
  differently on different platforms.
- The core syntax has no standard support for notes and warnings, tabs, a table of contents,
  cross-references, metadata, or content reuse. Tools add these features through extensions, and
  the extensions do not port between tools.
- Basic tables work, but cells with multiple paragraphs, code blocks, or lists are hard or
  impossible in some dialects. Wide tables are also hard to read in source.
- Structured authoring systems offer native snippet reuse, topic types, and conditional content.
  Plain-text markup needs extra tooling for each of these.
- Nested lists, indentation, and code blocks inside lists can behave unexpectedly, so source that
  looks right can render badly.
- Reviewers who are not used to plain text or Git may struggle, and the format has no built-in
  visual editing.
- Control over layout and styling is narrow. Finer control means embedding raw HTML, which mixes
  formats and can break in applications that sanitize HTML.
- The format offers several ways to do the same thing, which leads to inconsistency unless a
  linter enforces one.

## When it fits and when it does not

| Favors plain-text markup | Favors another format |
| --- | --- |
| Developer-heavy contributors | Many non-technical contributors |
| Docs as code, Git workflow | Need for visual editing |
| Generated reference plus hand-written guides | Heavy reuse, conditional content, or translation |
| Code samples tested in CI | Complex layouts or print-oriented design |
