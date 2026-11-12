# Natlu data — downloadable tafsir packs

Packs the Natlu app (`com.mushaf.reader`) downloads on request from its tafsir library and reads
offline. Each is a gzip-compressed SQLite file; `catalog.json` lists them with their SHA-256.

## Sources and licences

The packs come from two sources, each under its own licence:

- **Tafsir Center for Quranic Studies** — `ibn_kathir`, `tabari`, `baghawi`, `irab`: from its dataset
  ([tafsircenter/tafsir-mcp-data](https://huggingface.co/datasets/tafsircenter/tafsir-mcp-data), file `quran.db`), licensed
  [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribution: Tafsir Center for Quranic Studies (https://tafsir.net).
  What was changed is listed in [CORRECTIONS.md](CORRECTIONS.md) and made by the build tools in the app repository
  (`mushaf_app/tools/build_packs.py`, `pack_books.py`, `pack_common.py`). These packs carry the same licence.
- **OpenITI** — `qurtubi`, `shawkani`, `ibn_ashur`: from the [OpenITI](https://doi.org/10.5281/zenodo.3082463) corpus
  (release 2025.1.9), its versions taken from altafsir.com, licensed
  [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). Source files, pinned commits and changes are in
  [OPENITI.md](OPENITI.md); the build tools are `mushaf_app/tools/build_openiti_packs.py` and `openiti_tafsir.py`.
  These packs carry the same licence: no commercial use, and adaptations shared alike.

| Pack | Book | Version | Download | On device | SHA-256 |
|---|---|---|---|---|---|
| `ibn_kathir` | تفسير القرآن العظيم | 1 | 5.2 MB | 25.2 MB | `ad88919474a1be5c…` |
| `tabari` | جامع البيان عن تأويل آي القرآن | 1 | 7.8 MB | 39.3 MB | `240440d7d8b76c72…` |
| `baghawi` | معالم التنزيل | 1 | 3.4 MB | 17.3 MB | `a8ab7e5dad365f93…` |
| `irab` | إعراب القرآن الكريم | 1 | 1.9 MB | 16.3 MB | `5628c6291ccc3b03…` |
| `qurtubi` | الجامع لأحكام القرآن | 1 | 4.9 MB | 19.8 MB | `176d0dccedc6ab02…` |
| `shawkani` | فتح القدير | 1 | 3.1 MB | 12.8 MB | `4c6b23c702894791…` |
| `ibn_ashur` | التحرير والتنوير | 1 | 7.2 MB | 28.7 MB | `4a9f65b04a046978…` |

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
