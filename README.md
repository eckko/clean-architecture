# Clean Architecture: Recall Quiz

A practice quiz for the book *Clean Architecture*. It teaches the book's
ideas as concept cards with question ladders, brings back the questions you
miss sooner (spaced repetition) and keeps your progress in your browser
(and, when you sign in with Google, synced across your devices).

The site is served by GitHub Pages from this repository's `main` branch.

## What is in this repository

Only the book's own files. All the quiz code comes from the shared
template.

| Path | What it is |
|---|---|
| `index.html` | A tiny loader: shows the favicon and loads the quiz page and all code from the template on jsDelivr |
| `questions.json` | The question bank: 228 concepts, 1,423 questions |
| `images/` | The favicon (`favicon.png`) |
| `media/` | Encrypted pictures and figures used by cards and questions (`.enc`) |
| `book-structure/` | The chapter map the bank was built from |

## How the quiz code is loaded

`index.html` loads `js/boot.js` from one tagged copy of
[`eckko/recall-quiz-site-template`](https://github.com/eckko/recall-quiz-site-template)
on jsDelivr (`https://cdn.jsdelivr.net/gh/eckko/recall-quiz-site-template@TAG/`).
`boot.js` fetches the template's page from the same tag and starts it.
`questions.json`, `images/` and `media/` are still read from this site.

To move the book to a newer template, run this in a checkout of the
template, then commit the new `index.html`:

```
python3 tools/make_book_index.py NEW_TAG ../clean-architecture/index.html
```

Always use an exact tag (for example `2.1.0`), never a branch: a tag never
changes, so the site never changes under you.

## Change the questions

Edit `questions.json` and push to `main`; the site updates within a minute
or two. Never change a question's `id`: readers' saved progress is keyed
by it. The fields, the checks (`validate_bank.py`) and the style rules are
in the template repository (`README.md`, `ai-context/`, `tools/`).

## Try it on your computer

Open a terminal in this folder and run `python3 -m http.server`, then open
<http://localhost:8000/>. It needs an internet connection, because the code
comes from the CDN.
