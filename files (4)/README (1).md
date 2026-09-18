# CausePath

**Find where your skills matter most.**

CausePath matches your skills, interests, and availability to real
volunteer causes that need them — then points you to opportunities
near you. Built for **NextStep Hacks 2026**.

## The problem

A Gallup / Kettering Foundation study found that 54% of people who want
to volunteer say they simply don't know how to get started. The barrier
usually isn't time — it's not knowing where a specific skill set would
actually be useful. CausePath closes that gap.

## What it does

1. You pick your skills (17 options), the causes you care about (14
   categories), your availability, and your preferred format
   (in-person/remote).
2. CausePath scores 26 real volunteer opportunity archetypes against
   your answers — weighing cause alignment and skill overlap most
   heavily, with availability and format as secondary factors.
3. Your top 5 matches are shown with a visual match-percentage ring,
   a plain-language explanation of why each one fits, and a
   "Find this near you" link that opens a real local search.

No sign-up, no data collection. Everything runs client-side in the
browser — nothing you type is stored or sent anywhere.

## Tech stack

Plain **HTML, CSS, and JavaScript** — no frameworks, no build step,
no backend, no external API calls. This was a deliberate choice: it
keeps the matching logic fully transparent and auditable, and means
the whole project can be hosted anywhere for free, forever.

## Project structure

```
causepath/
├── index.html            # Everything: markup, styles, and matching logic
├── favicon.svg            # Browser tab icon
├── DEVPOST_WRITEUP.md      # Full hackathon submission write-up
└── README.md               # This file
```

Everything lives in `index.html` by design, since the project has no
build step — open it directly in a browser, or deploy it as a static
site.

## Running it locally

No installation needed. Either:

- Double-click `index.html` to open it directly in your browser, or
- Serve it locally for a closer-to-production feel:

  ```bash
  python3 -m http.server 8000
  # then open http://localhost:8000
  ```

## Deploying it

This is a static site, so any static host works. The version used for
the hackathon demo was deployed via
[Netlify Drop](https://app.netlify.com/drop) — drag the folder in and
it's live in seconds.

## How the matching algorithm works

Each opportunity in the database lists the skills it values, the cause
category it belongs to, when it typically runs, and its format. When
you submit the form, every opportunity is scored against your answers:

- **+2 points** per skill you selected that the opportunity also lists
- **+5 points** if the opportunity's cause category matches one you picked
- **+2 points** if your availability is compatible
- **+2 points** if your format preference is compatible

Scores are normalized to a percentage of the opportunity's maximum
possible score, then the top 5 are shown. Cause alignment is weighted
most heavily on purpose — volunteering for something you don't care
about rarely sticks, even if your skills are a perfect fit.

## Testing

The matching logic was tested directly with Node (outside the browser)
to confirm:

- Every skill and cause ID referenced by an opportunity actually exists
  in the skills/causes lists (no silent typos breaking a match)
- Every cause category has at least one matching opportunity (no
  dead-end selections)
- Sample inputs produce sensibly ranked results

## What's next

- Pull from real, regularly updated local volunteer listings instead
  of static search links
- Add a "save my matches" feature
- Partner with local volunteer coordination nonprofits to validate and
  expand the opportunity list

## License

Built as a hackathon project for NextStep Hacks 2026. Not affiliated
with any organization or listing mentioned in the app.
