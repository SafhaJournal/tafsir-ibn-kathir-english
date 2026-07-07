# Contributing

Thank you for helping improve this translation. The goal is a faithful, freely-usable English
Tafsir Ibn Kathir — and community corrections are how it gets there.

## The one rule that keeps this project alive

> **Base every correction on the Arabic source — never on another English translation.**

This corpus is valuable *because* it is provably independent of any copyrighted translation (see
[PROVENANCE.md](PROVENANCE.md)). If corrections were copied in from a copyrighted English edition,
that independence — and everyone's freedom to reuse the text — would be compromised. So:

- ✅ **Do** ground your fix in the Arabic wording, grammar, and meaning.
- ✅ **Do** cite the Arabic phrase you're correcting against.
- ❌ **Don't** paste or paraphrase text from a copyrighted English translation (Ibn Kathir or otherwise).
- ❌ **Don't** submit a fix whose only justification is "another translation says X."

Reference grammars, dictionaries (Lane, Hans Wehr), and the Qur'anic Arabic itself are all fine.

## What a good correction looks like

Include:

1. **Location** — surah:ayah (e.g. `2:255`).
2. **Current text** — the English phrase you think is wrong.
3. **Arabic anchor** — the Arabic word/phrase it should reflect.
4. **Proposed correction** — your suggested English.
5. **Why** — the grammatical or lexical reason (root, case, referent, idiom, etc.).

## How to submit

- **Small fix:** open an **Issue** using the *Translation correction* template — fastest, and we
  can discuss before editing.
- **Direct edit:** open a **Pull Request** editing the relevant file in `surahs/`. Keep each PR
  focused (one passage or one theme). Don't hand-edit `corpus/*.jsonl` — it's regenerated from the
  source translations; fix the `surahs/` text and note it, and the corpus will be rebuilt.

## Style conventions (match the existing text)

- `ﷺ` is used for the Prophet Muhammad; `(peace be upon him)` / `(peace be upon them both)` for
  other prophets. **`ﷺ` is for Muhammad only.**
- Qur'anic verses go in `{curly braces}`.
- Chains of narration are compressed as `[chain] ...`.
- Transliterated terms are glossed in plain parentheses on first use.
- No em dashes (use periods, commas, or brackets); Latin + Arabic script only.

## Scope

This project corrects **fidelity to the Arabic** and clear English. It is not the venue for
theological debate or for re-translating to a different school's preference where the Arabic is
genuinely ambiguous — in ambiguous cases, we favor what the Arabic most plainly supports and may
note alternatives.

## Conduct

This is religious material maintained by volunteers. Be respectful and precise. Assume good faith.
