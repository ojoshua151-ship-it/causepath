# CausePath — Find where your skills matter most

**Built for NextStep Hacks 2026** | Category fit: Beginner Friendly · Machine Learning/AI · Social Good

## Inspiration

A Gallup and Kettering Foundation study of over 20,000 Americans found that the
biggest reason people who *want* to volunteer never do isn't free time —
it's that 54% of would-be volunteers simply don't know how to get involved.
Meanwhile, nonprofits across every cause area are chronically short-staffed
and could put almost any skill to use, from cooking to coding.

That gap — willing people on one side, real unmet need on the other, and no
simple bridge between them — is exactly what CausePath is built to close.

## What it does

CausePath asks you three simple things: what skills you can offer, what
causes you care about, and when/how you're available. It then scores your
answers against a database of 26 real volunteer opportunity types — things
like community garden work, tutoring, senior companion visits, animal
shelter support, and more — and shows you your top 5 matches, each with:

- A visual match-percentage ring
- A plain-language explanation of *why* it's a good fit for you specifically
- A one-click "Find this near you" button that opens a real search for that
  opportunity in your area

No account, no data collection — everything runs client-side in your browser,
and nothing you type is stored or sent anywhere.

## How we built it

CausePath is built with plain HTML, CSS, and JavaScript — no frameworks,
no backend, and no external API calls, which kept it fast, free to run,
and easy to deploy as a static site.

The matching engine is a transparent, weighted scoring algorithm: each
opportunity earns points for skill overlap, cause alignment, and
availability/format compatibility, and the top-scoring matches are surfaced
to the user. We chose a rule-based approach over calling a large language
model specifically so the logic stays auditable — anyone can look at the
code and see exactly why a match scored the way it did, which matters for
a tool meant to build trust with first-time volunteers.

## Challenges we ran into

As a newer developer, structuring a scoring algorithm that felt fair across
very different opportunity types (a remote marketing role vs. an in-person
shelter shift) took some iteration — early versions over-weighted skill
overlap and under-weighted whether someone actually cared about the cause.
We rebalanced the scoring so cause alignment carries the most weight, since
volunteering someone doesn't care about rarely sticks.

## Accomplishments we're proud of

- A fully working matching algorithm that we tested directly (not just
  visually) — running real inputs through the scoring logic in Node to
  confirm it ranks sensibly and that every skill/category reference in the
  data is valid
- A clean, accessible UI with animated feedback (loading state, progress
  rings, staggered card reveals) that makes a simple tool feel polished
- Zero dependencies, zero API costs, and zero data collection — this can
  run forever for free

## What we learned

Building the scoring system taught us a lot about how to translate a fuzzy
human idea ("what fits me?") into something a simple algorithm can reason
about consistently. We also learned the value of testing logic in isolation
before trusting it inside a UI — several scoring edge cases only became
obvious once we ran real test inputs through the algorithm directly.

## What's next for CausePath

- Keep expanding the opportunity database further, ideally pulling
  from real, regularly updated local listings instead of static search links
- Add a saved-matches feature so people can revisit opportunities later
- Explore optional AI-assisted matching for users with very specific or
  unusual skill combinations that don't map cleanly to the fixed categories
- Partner with local volunteer coordination nonprofits to validate the
  opportunity list against what's actually needed on the ground

## Built with

HTML, CSS, JavaScript — no frameworks, no backend, no external APIs.
