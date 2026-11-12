# Packs from OpenITI

These packs are built from the OpenITI corpus (release 2025.1.9,
[https://doi.org/10.5281/zenodo.3082463](https://doi.org/10.5281/zenodo.3082463)), licensed [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). The texts are
OpenITI's versions taken from altafsir.com, already divided by the ayahs they explain, with
introductions and footnotes removed. The packs are adapted from them by
`mushaf_app/tools/build_openiti_packs.py` and `openiti_tafsir.py` in the app repository, and carry
the same licence. They are used in a free app with no advertising and nothing for sale.

| Pack | Book | Author | Source file (pinned commit) |
|---|---|---|---|
| `qurtubi` | الجامع لأحكام القرآن | القرطبي | [0671AbuCabdAllahQurtubi.JamicLiAhkamQuran.Tafsir01005-ara1](https://github.com/OpenITI/0675AH/blob/d98a982f2be9b26ad8cc8300ca774363aaadb4e4/data/0671AbuCabdAllahQurtubi/0671AbuCabdAllahQurtubi.JamicLiAhkamQuran/0671AbuCabdAllahQurtubi.JamicLiAhkamQuran.Tafsir01005-ara1) |
| `shawkani` | فتح القدير | الشوكاني | [1255Shawkani.FathQadir.Tafsir01009-ara1](https://github.com/OpenITI/1275AH/blob/42a9fd4aea99aebd2f85f1bc3e5db737283c7f14/data/1255Shawkani/1255Shawkani.FathQadir/1255Shawkani.FathQadir.Tafsir01009-ara1) |
| `ibn_ashur` | التحرير والتنوير | محمد الطاهر ابن عاشور | [1393MuhammadTahirIbnCashurTunisi.TahrirWaTanwir.Tafsir07054-ara1](https://github.com/OpenITI/1400AH/blob/9ecd69d142e2f165f80a52a958aa2cda09048e03/data/1393MuhammadTahirIbnCashurTunisi/1393MuhammadTahirIbnCashurTunisi.TahrirWaTanwir/1393MuhammadTahirIbnCashurTunisi.TahrirWaTanwir.Tafsir07054-ara1) |

## ما غُيّر

- **تفسير القرطبي:** وُصلت أسطر الطبعة المقطوعة، وحُذفت علامات التقسيم التي يضعها المشروع، ووُضعت الآيات المقتبسة في فقرة مستقلة بين قوسين مع موضعها. ولا يتضمن المصدر شرح الآية ٥٦ من سورة الأحزاب، فوُضعت في موضعها عبارة تبيّن ذلك.
- **فتح القدير:** وُصلت أسطر الطبعة المقطوعة، وحُذفت علامات التقسيم التي يضعها المشروع، ووُضعت الآيات المقتبسة في فقرة مستقلة بين قوسين مع موضعها. ومقطعان في المصدر يشملان الآية ١٢٥ من البقرة، فجُعل الثاني يبدأ بالآية ١٢٦.
- **التحرير والتنوير:** وُصلت أسطر الطبعة المقطوعة، وحُذفت علامات التقسيم التي يضعها المشروع، ووُضعت الآيات المقتبسة في فقرة مستقلة بين قوسين مع موضعها. وصُحح حرف مكرر في موضع واحد.
