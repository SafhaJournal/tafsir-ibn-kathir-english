# Corpus format

`ibn-kathir-en-safha.jsonl` — one JSON object per line, one line per commentary block, in
surah/ayah order. 6,236 records across all 114 surahs.

## Row schema

| field | type | meaning |
|---|---|---|
| `edition_id` | string | `ibn-kathir-en-safha` |
| `edition_type` | string | `tafsir` |
| `lang` | string | `en` |
| `source_edition` | string | id of the public-domain Arabic source |
| `surah` | int | surah number (1–114) |
| `ayah` | int | ayah number |
| `ayah_key` | string | `"<surah>:<ayah>"`, e.g. `"2:255"` |
| `block_id` | int | id of the commentary block within the surah |
| `block_key` | string | `"<surah>:<block_id>"` — globally unique |
| `covers` | string | the ayah range this block comments on, e.g. `"2:1-5"` |
| `is_shared` | bool | true if several ayat share this one block of commentary |
| `content` | string | the English tafsir text |
| `translator_model` | string | provenance |
| `generated_at` | string | timestamp |
| `status` | string | `machine` (see below) |
| `pipeline` | string | provenance |

## Important: grouped ayat

Ibn Kathir often comments on a **group** of ayat at once. Those ayat each get their own row, but
they all carry the **same** `content` and the same `block_key`. If you are indexing or embedding,
**dedup on `block_key`** so you don't process the same commentary multiple times. Use `covers` and
`is_shared` to render a shared commentary once across its ayat.

## `status`

`machine` means: AI-translated and machine-graded (surahs 2–77 additionally received a
human-verified fidelity pass). It has not been through formal scholarly review. If you build a
review workflow, you can advance rows to your own `verified` / `reviewed` states downstream.

## No quality scores here — by design

This served corpus intentionally contains **no fidelity scores, verdicts, or grader notes** — only
the translation and its provenance. Per-surah quality is summarized in [`../QUALITY.md`](../QUALITY.md).
