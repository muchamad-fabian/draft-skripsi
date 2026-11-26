# Data Iqro — Citra Canvas Tulisan Hijaiyah

Kumpulan tangkapan layar (*screenshot*) hasil ekspor *canvas* digital untuk kosakata **Iqro 3**.
Dataset ini menjadi bahan awal perancangan dataset pada penelitian pengenalan tulisan tangan
huruf Hijaiyah bersambung (CNN-LSTM + transfer learning MobileNetV3).

## Ringkasan

- **Jumlah berkas:** 112 citra `.png`
- **Total ukuran:** ± 396 KB
- **Format:** PNG (citra 2D hasil ekspor canvas, latar putih, goresan gelap)
- **Penamaan berkas:** mengikuti *timestamp* screenshot, mis. `Screenshot_2026-11-25_135241.png`

## Struktur Folder

Nama folder mengikuti pola `page-<halaman>-<jumlah huruf>` atau `2 hjjah <awal>-<akhir>`
(rentang halaman pada buku Iqro 3). Akhiran `done` menandai folder yang sudah lengkap terisi.

| Folder | Jumlah Citra |
|---|---|
| `2 hjjah 1-4 done` | 4 |
| `2 hjjah 2-4` | 4 |
| `2 hjjah 3-5` | 5 |
| `2 hjjah 4-4` | 4 |
| `2 hjjah 5-4` | 4 |
| `2 hjjah 6-4` | 4 |
| `2 hjjah 7-4` | 4 |
| `2 hjjah 8-5` | 5 |
| `page-3-8` | 8 |
| `page-4-12` | 12 |
| `page-5-6 done` | 6 |
| `page-7-8` | 8 |
| `page-9-6` | 6 |
| `page-10-7` | 7 |
| `page-12-2` | 2 |
| `page-13-1` | 1 |
| `page-16-14` | 14 |
| `page-17-6` | 6 |
| `page-19-4` | 4 |
| `page-21-4 done` | 4 |

## Catatan

- Data ini masih mentah (*raw*): belum dilabeli per karakter dan belum melalui tahap
  *preprocessing* (normalisasi ukuran, *binarization*, dsb.).
- Folder `Pengerjaan/Data per-hjjah/Hijja2/` (dataset besar ± 227 MB) tetap tidak disertakan
  di repositori ini sesuai `.gitignore`.
