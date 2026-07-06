# API101 Textbook

Static interactive textbook modules for Harvard Kennedy School's API101 course. This repository contains only the files needed to host the public site.

## Site Structure

- `index.html`: landing page and module path
- `chapters/`: module pages and practice quiz pages
- `css/theme.css`: shared site styling
- `js/textbook.js`: shared interactive components, graphing behavior, quizzes, glossary, flashcards, and sidebar behavior
- `assets/images/`: images used by the site
- `assets/quizzes/`: JSON question banks loaded by the practice quiz pages

The site has no build step and no server-side code. It is plain HTML, CSS, and JavaScript. Runtime dependencies such as D3 and KaTeX are loaded from CDNs in the chapter HTML files.

## Local Preview

From the repository root:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

Use a local server instead of opening files directly, because quiz JSON files are fetched by browser JavaScript.

## Maintenance Notes

- Edit module text directly in the relevant file under `chapters/`.
- Edit shared layout, graphing, quiz rendering, glossary, flashcards, and repeated instructional text in `js/textbook.js`.
- Edit shared visual styles in `css/theme.css`.
- Edit quiz content in `assets/quizzes/*.json`; keep the files valid JSON.
- If browser caching hides CSS changes after deployment, update the stylesheet query string in the HTML files, for example `theme.css?v=4`.
- Keep this repository focused on hosted runtime files. Do not add review notes, source exports, local tooling, or draft materials unless they are intentionally meant to be public.

## Recommended Checks

Before pushing content changes:

```bash
node --check js/textbook.js
python3 -m json.tool assets/quizzes/module1-quiz.json > /dev/null
git diff --check
```

For quiz edits, run the JSON check on each file changed.

## Acknowledgments

This project was developed with contributions from Pinar Doğan, Juan Saavedra, Jacob Jameson, Mae Klinger, and Maria Flanagan.
