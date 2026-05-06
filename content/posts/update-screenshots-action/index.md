---
title: "GitHub Action To Automate Screenshots"
date: 2026-05-06
description: "A small GitHub Action I built to capture site screenshots and keep Markdown docs in sync."
pageNumber: "210"
---

I built [update-screenshots-action](https://github.com/Mrchazaaa/update-screenshots-action) to solve a small but recurring documentation problem: screenshots in READMEs look useful right up until they go stale. I wanted a simple way to capture a page, write the image back into the repository, and update a known section of a Markdown file without having to maintain a custom script in every project that needed it.

The action takes a URL, opens it in Chromium through Playwright, captures either a PNG or an animated GIF, and writes the result to a repo-relative path. It then rewrites a marked block in a Markdown file so the screenshot reference stays in sync with the generated asset. I also added optional commit-and-push support, which makes it practical to run on a schedule or after changes to a site without extra workflow glue around the action itself.

What I like about this project is that it stays narrow. It is not trying to be a general documentation pipeline or a visual regression tool. It does one job: keep a screenshot current and wire that screenshot into Markdown in a predictable way. That constraint made the implementation cleaner, and it also forced me to think about awkward operational details that matter in CI, like retrying navigation while a local preview server starts up and only committing the managed files when something actually changed.

At the time of writing, this portfolio repository uses that action in its own workflow to refresh the homepage image shown in the root README, which is exactly the kind of reuse I was aiming for. The action repository also uses the action on itself for the demo screenshot, so the project doubles as its own example and a check that the workflow holds up in practice.

[View the project on GitHub](https://github.com/Mrchazaaa/update-screenshots-action)
