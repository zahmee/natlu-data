# Natlu data — downloadable tafsir packs

Packs the Natlu app (`com.mushaf.reader`) downloads on request from its tafsir library and reads
offline. Each is a gzip-compressed SQLite file; `catalog.json` lists them with their SHA-256.

## Source and licence

All texts come from the Tafsir Center for Quranic Studies' dataset
([tafsircenter/tafsir-mcp-data](https://huggingface.co/datasets/tafsircenter/tafsir-mcp-data), file `quran.db`), licensed
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribution: Tafsir Center for Quranic Studies (https://tafsir.net).
The packs are adapted from it; what was changed is listed in [CORRECTIONS.md](CORRECTIONS.md) and
made by the build tools in the app repository (`mushaf_app/tools/build_packs.py`, `pack_books.py`,
`pack_common.py`). These files carry the same licence.

| Pack | Book | Version | Download | On device | SHA-256 |
|---|---|---|---|---|---|
| `ibn_kathir` | تفسير القرآن العظيم | 1 | 5.2 MB | 25.2 MB | `ad88919474a1be5c…` |
| `tabari` | جامع البيان عن تأويل آي القرآن | 1 | 7.8 MB | 39.3 MB | `240440d7d8b76c72…` |
| `baghawi` | معالم التنزيل | 1 | 3.4 MB | 17.3 MB | `a8ab7e5dad365f93…` |
| `irab` | إعراب القرآن الكريم | 1 | 1.9 MB | 16.3 MB | `5628c6291ccc3b03…` |

## Pack format (schema 1)

```
pack_meta(key TEXT PRIMARY KEY, value TEXT)
    passage(row_id INTEGER PRIMARY KEY, group_id, surah, from_ayah, to_ayah, kind, text, notes)
    ayah_group(ayah_key INTEGER PRIMARY KEY, group_id)        -- tafsir packs
    ayah_text(ayah_key INTEGER PRIMARY KEY, text, notes)      -- per-ayah text packs (i'rab)

where ayah_key = surah * 1000 + ayah. `passage.kind` holds the same Arabic row types as the bundled
database, so the app reads both with one mapping. `text` may carry note anchors ⟦n⟧; `notes` holds
the shown notes, one per line, in anchor order.
```
