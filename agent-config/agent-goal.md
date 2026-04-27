# Agent Goal

## Purpose
Temukan keyword gap antara openjournaltheme.com dan kompetitor-kompetitornya secara otomatis, lalu simpan laporan detail berisi peluang keyword yang belum dioptimalkan oleh situs.

## Input
- **Ubersuggest**: Data keyword, volume pencarian, difficulty, dan peringkat kompetitor
- **PostHog**: Data perilaku pengunjung situs (halaman populer, sumber traffic, konversi) untuk konteks prioritas keyword
- **Kompetitor**: Ditemukan otomatis oleh agent berdasarkan analisis Ubersuggest (tidak didefinisikan manual)

## Output
- Laporan detail keyword gap disimpan otomatis sebagai file Markdown di folder `reports/`
- Format laporan mencakup:
  - Daftar kompetitor yang ditemukan
  - Keyword yang diperingkat kompetitor tapi tidak oleh openjournaltheme.com
  - Volume pencarian, difficulty, dan estimasi traffic per keyword
  - Rekomendasi prioritas berdasarkan peluang vs persaingan
  - Konteks dari data PostHog (halaman mana yang relevan untuk dioptimalkan)

## Autonomy Level
**Auto** — Agent menyimpan laporan secara otomatis tanpa memerlukan persetujuan. Laporan dapat ditinjau setelah disimpan.

## Additional Context
- Bisnis bergerak di niche OJS/academic publishing — keyword harus relevan dengan topik: OJS theme, OJS hosting, OJS plugin, open journal systems, academic journal publishing
- Fokus pada keyword berbahasa Inggris (pasar internasional)
- Laporan diberi nama dengan timestamp: `reports/keyword-gap-YYYY-MM-DD.md`
