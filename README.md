# Skripsi — Klasifikasi Multi-Label Huruf Hijaiyah Sambung

**Judul:** Klasifikasi Multi-Label untuk Pengenalan Huruf Hijaiyah Sambung Menggunakan Transfer Learning
**Penulis:** Muchamad Budi Fabiantoro (NIM: 22314050111003)
**Program Studi:** Informatika, Fakultas Teknologi dan Industri, Universitas Internasional Semen Indonesia (UISI)
**Dosen Pembimbing:** Pak Zain

## Ringkasan

Penelitian ini mengembangkan model pengenalan tulisan tangan huruf Hijaiyah **bersambung** (2–3 karakter per citra) dengan pendekatan **nirsegmentasi** (*segmentation-free sequence recognition*) berbasis **CNN-LSTM** dan **transfer learning** (*backbone* MobileNetV4).

- **Masukan:** citra digital tunggal hasil ekspor *canvas* interaktif, kosakata mengacu materi **Iqro 3**.
- **Keluaran:** urutan 28 huruf Hijaiyah tanpa harakat.
- **Metrik evaluasi:** akurasi urutan penuh (*exact sequence match*), akurasi per karakter, dan *Character Error Rate* (CER).

Latar belakang dan celah penelitian lengkap ada di [`BAB1_PENDAHULUAN.md`](BAB1_PENDAHULUAN.md).

## Isi Repositori

| Berkas / Folder | Keterangan |
|---|---|
| `BAB1_PENDAHULUAN.md` | Naskah Bab 1 (Pendahuluan) beserta ringkasan analisis draf |
| `prd.md` | Product Requirements Document — spesifikasi teknis pipeline |
| `FORMAT_TUGAS_AKHIR.md` | Format/lembar resmi tugas akhir (template kampus) |
| `Pengerjaan/` | Arsip catatan sesi kerja (status, keputusan teknis, langkah lanjut) |
| `.opencode/` | Konfigurasi tool lokal |

### Arsip sesi

`Pengerjaan/sesiAnalis-2026-09-28/` berisi catatan penutup sesi agar pekerjaan bisa dilanjutkan tanpa menebak state sebelumnya:

- `STATUS_SESI.md`, `CATATAN_TEKNIK.md`, `LANGKAH_LANJUT.md`, `RENCANA_NOTEBOOK_COLAB.md`, `CHECKLIST_RESUME.md`, `MANIFEST_SESI.json`

**Aturan melanjutkan:** baca `STATUS_SESI.md` lebih dulu; jangan menjalankan operasi penghapusan massal (`git clean`, `git reset --hard`, dsb.); jangan menganggap metrik data demo sebagai hasil skripsi.

## Catatan: Materi Lokal (Tidak di-push)

Beberapa berkas materi skripsi **sengaja** tidak disertakan di repositori ini (lihat `.gitignore`), yaitu draf proposal, analisis literatur, kumpulan PDF referensi, gambar, dan catatan riset. Berkas-berkas tersebut hanya tersimpan lokal. Jika dibutuhkan untuk reproduksi, mintakan langsung kepada penulis.
