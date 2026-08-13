# Art vs. Artist

**Does knowing about a TV creator's misconduct change how much audiences enjoy their show?**

A free, anonymous, browser-based experiment built for an undergraduate research-methods project
(ENGL 1102, University of the People).

**Live site: https://sardelka553.github.io/art-vs-artist/**

---

## What this is

Psychology experiments have shown that learning something bad about a painter makes people like
their paintings less - but the effect has almost never been tested on **television**, where a show
is made by hundreds of people and a story pulls you in. This site runs that experiment.

Each visitor is randomly assigned to one of two groups:

| Group | What they read before each clip |
|---|---|
| **Control** | Neutral production background: when the show aired, who made it, how it was filmed |
| **Informed** | A short, sourced account of a documented controversy involving the show's creator |

Both groups then watch the **same three clips** (drawn at random from eight shows) and rate each on
five 1-7 scales. Afterwards they answer one open-ended question, get a full debrief, and see the
live aggregated results.

## Features

- **Genuinely anonymous.** No name, email, IP address, login, or tracking cookie. Age is a broad
  band and location a world region, so no combination of answers identifies anyone.
- **Proper randomisation** using `crypto.getRandomValues`, for both group assignment and clip draw.
- **Matched-length stimuli** (~95 words per text) so reading time isn't a confound.
- **Live dashboard** rendered the moment a visitor submits: accessible hand-built SVG charts with
  hover tooltips, a table view for every chart, light/dark themes, and a CSV export.
- **No dependencies.** One HTML file. No frameworks, no CDN, no build step needed to run it.
- **Free forever.** GitHub Pages for hosting, Google Apps Script + Sheets for storage.

## How it fits together

```
index.html   the whole site, self-contained
.nojekyll    stops GitHub processing the site with Jekyll
```

Responses POST to a Google Apps Script web app bound to a private Google Sheet. The same endpoint
returns aggregated statistics for the dashboard. It only ever returns **aggregates** plus the
free-text answers whose authors explicitly ticked "yes, quote me" - raw participant rows are never
exposed publicly.

The spreadsheet has two tabs:

- `participants` - one row per person: timestamp, random ID, condition, nickname, age band,
  region, viewing frequency, duration, quote consent, open-ended answer.
- `responses` - one row per clip rated: the five 1-7 scores plus two covariates (had they seen the
  show, did they already know about the controversy).

## A note on the background texts

The informed-condition texts describe real allegations against real people, so they were written to
a strict standard:

- every allegation is attributed to a named accuser or a named publication;
- contested claims are hedged ("alleged", "reported that") and never stated as fact;
- each person's response - denial, apology, or admission - is reported alongside the accusation;
- characterisations such as "racist" appear only as quoted, attributed language;
- two free-to-read reputable sources are linked for every case, and shown to participants.

If you think a text is inaccurate, please open an issue. Corrections are welcome.

## Clip credits

All clips are embedded from official rights-holder channels on YouTube and are not hosted here.

## Licence

Code is free to reuse. The study materials are coursework - please credit if you build on them.
