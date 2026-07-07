# Tafsir Ibn Kathir — English (open, copyright-clean)

A **complete English translation of Tafsir Ibn Kathir** — all 114 surahs — generated
independently from the **public-domain Arabic** and released under **CC BY 4.0**. Free to
read, use, embed in apps, and improve.

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](LICENSE)
· 114 surahs · 6,236 commentary records · English

> **This is a working library, not a finished one.** No claim is made that every rendering is
> 100% correct. Every passage has been machine-verified against the Arabic (and much of it
> human-checked), but errors certainly remain — and finding them is a community effort by
> design. **If you see something wrong, please [open an issue or PR](CONTRIBUTING.md).** One
> correction here fixes it for every reader and every app, forever.

---

## Why this exists

If you've tried to build anything with an English *tafsir* — an app, a study tool, a dataset —
you've probably hit the same wall: **the good English translations of Ibn Kathir are
copyrighted.** You can read them, but you can't freely redistribute them, ship them in a
product, or build on them.

The Arabic Ibn Kathir, though, has been in the **public domain for over 600 years** (the author
died in 1373 CE). So the roadblock isn't the tafsir — it's the *English*. This project removes
that roadblock by producing a **new** English translation straight from the public-domain
Arabic, with an architecture specifically designed so the result is *provably independent* of
any copyrighted translation. See **[PROVENANCE.md](PROVENANCE.md)** for the full record.

If you hit this wall too — here's a way through, and you're welcome to it.

## Why a library, not live generation

There's a second reason this project exists. Apps are increasingly wiring AI straight into
their products — and for religious text, generating commentary *on the fly* is a real problem.
Every request is a fresh roll of the dice: the same verse can be explained differently every
time, sometimes faithfully, sometimes subtly wrong — and when it's wrong, the error vanishes
with the response. Nobody can review what a thousand users were each individually told. There
is nothing to check, nothing to cite, nothing to fix.

A static library inverts that:

- **Generated once, verified once, read by everyone.** Every passage here went through the same
  translation-and-verification pipeline (see [PROVENANCE.md](PROVENANCE.md)) *before*
  publication — nothing is improvised in production.
- **Errors are findable and fixable.** The text is public and stable. When someone spots a
  mistake, one correction fixes it for every app and every future reader (see
  [CONTRIBUTING.md](CONTRIBUTING.md)). A live model's mistake can't even be found afterward —
  it just happens again, differently, for someone else.
- **Apps can pin and cite.** An application shipping this library knows exactly what its users
  will read, can pin a version, and can point back to this repository's record. *"What did the
  AI tell my users last month?"* has an answer here. With on-the-fly generation, it has none.

In short: **AI helped build this library; it does not run it.** What you read is fixed,
reviewed, and correctable — which is the standard religious commentary deserves.

## What's inside

| Path | What it is |
|---|---|
| **`surahs/`** | Human-readable translation, one file per surah, **English + Arabic side by side.** Browse it right here on GitHub. |
| **`corpus/ibn-kathir-en-safha.jsonl`** | The machine-readable corpus — one JSON object per commentary block. See [`corpus/README.md`](corpus/README.md). |
| **[`PROVENANCE.md`](PROVENANCE.md)** / `provenance.json` | The copyright & independence record: source, method, and measured evidence that this is not copied. |
| **[`QUALITY.md`](QUALITY.md)** | Per-surah fidelity scores — honest about where it's strong and where it needs eyes. |
| **[`CONTRIBUTING.md`](CONTRIBUTING.md)** | How to submit corrections (grounded in the Arabic). |

## How it was made (short version)

Three separated roles, so the translation can never have copied a copyrighted one:

1. **Translator** (an AI model) saw the **Arabic only** — it never, at any point, read any
   English translation — and translated from scratch.
2. **Examiner** (a *different* company's AI model) checked each finished surah against the
   **Arabic** for accuracy. Because AI can hallucinate — inventing a meaning, garbling a ruling,
   or misreading a rare word — the examiner also consulted a published, scholar-reviewed English
   edition as a **verification benchmark**: a way to detect where the AI's rendering diverged
   from meanings scholars have already established. That comparison was internal only, compared
   *meaning* rather than wording, and none of that edition's text was ever copied into the
   output. The examiner's feedback points back to the Arabic, never to the reference's wording.
3. **A plain-code measuring machine** counts verbatim overlap with the reference as a paper
   trail proving the wording is independent.

Result: across all 114 surahs, **~91% of four-word prose sequences do not appear in the
reference at all** (mean 4-gram overlap 8.8%). The little overlap that exists is unavoidable
shared material — Qur'anic verse wording, proper names, isnad chains, standard honorifics.
Full method and evidence: **[PROVENANCE.md](PROVENANCE.md)**.

## Honest limitations — read this before relying on the text

**No claim of perfection is made here.** This is a working library: published early so it can
be used, checked, and improved in the open — not held back until some imagined day it is
flawless.

- **It's AI-generated**, then machine-graded, and surahs 2–77 got an additional line-by-line
  human-verified fidelity pass. It is **not** a substitute for a qualified scholar's translation,
  and it should not be treated as one.
- **Errors certainly remain.** Verification catches much, not everything — a rare word, a subtle
  referent, an idiom can still slip through. Where precision matters (rulings especially),
  verify against the Arabic and consult qualified scholars.
- Quality scores are the automated examiner's; treat them as a guide, not gospel.
- **Corrections are the whole point.** Every reader who checks a passage against the Arabic
  makes the library better than any AI pipeline could alone. If you see something — even a
  small thing — **please say something**: open an issue or PR (see below). This library is
  meant to get *better* every year, and that only happens with you.

## Using it

**Read:** open any file in [`surahs/`](surahs/).

**Load the data:** each line of `corpus/ibn-kathir-en-safha.jsonl` is one commentary block:

```json
{ "surah": 2, "ayah": 255, "ayah_key": "2:255", "block_key": "2:255",
  "covers": "2:255", "is_shared": false, "content": "…the English tafsir…", "lang": "en" }
```

Ibn Kathir comments on *groups* of ayat, so grouped ayat share one block — dedup on `block_key`.
Details in [`corpus/README.md`](corpus/README.md).

## Contributing corrections

Found a spot where the English doesn't match the Arabic? **Please open an issue or PR.** One
rule keeps this corpus reusable by everyone: **base every correction on the Arabic source, never
on another (copyrighted) English translation.** That's what keeps the whole thing clean-room and
CC-BY-shareable. See **[CONTRIBUTING.md](CONTRIBUTING.md)**.

Maintained by **Yvette Z**. The best way to reach me is by opening a **GitHub Issue** (use the
*Translation correction* template for fixes). For anything that doesn't fit an issue, email
**developers@safhajournal.com**.

## License

Translations: **[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE)** — use it
anywhere, including commercially; just credit this project.

The underlying Arabic Tafsir Ibn Kathir is in the **public domain**.

## Acknowledgements

- Arabic source: Tafsir Ibn Kathir via QUL resource 22, mirrored by
  [`spa5k/tafsir_api`](https://github.com/spa5k/tafsir_api).
- Built with a blind-translation + independent-grading pipeline (the "Safha tafsir grader").

## A note

This is religious commentary. It's offered in good faith to make Ibn Kathir's tafsir freely
usable in English; please treat it accordingly, verify against the Arabic, and consult qualified
scholars for matters of religious ruling. Nothing here is legal advice.
