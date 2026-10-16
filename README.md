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
| `DRAFT_PROPOSAL_SKRIPSI.md` | Draf lengkap proposal skripsi |
| `ARSIP_DRAFT_BAB1_PROPOSAL.md` | Arsip draf awal Bab 1 / proposal |
| `ANALISIS_LITERATUR_LENGKAP.md` | Analisis literatur lengkap |
| `literatur_gap_skripsi.md` | Pemetaan *research gap* |
| `skripsi_hijaiyah_canvas_research_notes.md` | Catatan riset canvas Hijaiyah |
| `DAFTAR_JURNAL_REFERENSI.md` | Daftar jurnal acuan |
| `prd.md` | Product Requirements Document — spesifikasi teknis pipeline |
| `FORMAT_TUGAS_AKHIR.md` | Format/lembar resmi tugas akhir (template kampus) |
| `file GAP/` | Kumpulan PDF jurnal pendukung & kajian *research gap* |
| `file pdf/` | PDF acuan (materi Iqro 3, ketentuan penulisan skripsi UISI) |
| `panduan-penulisan-skripsi.pdf` | Panduan penulisan skripsi |
| `Pengerjaan/` | Arsip catatan sesi kerja (status, keputusan teknis, langkah lanjut) |
| `.opencode/`, `.qoder/` | Konfigurasi tool lokal |

### Arsip sesi

`Pengerjaan/sesiAnalis-2026-09-28/` berisi catatan penutup sesi agar pekerjaan bisa dilanjutkan tanpa menebak state sebelumnya:

- `STATUS_SESI.md`, `CATATAN_TEKNIK.md`, `LANGKAH_LANJUT.md`, `RENCANA_NOTEBOOK_COLAB.md`, `CHECKLIST_RESUME.md`, `MANIFEST_SESI.json`

**Aturan melanjutkan:** baca `STATUS_SESI.md` lebih dulu; jangan menjalankan operasi penghapusan massal (`git clean`, `git reset --hard`, dsb.); jangan menganggap metrik data demo sebagai hasil skripsi.

## Catatan: Berkas yang Tidak Disertakan

Agar repositori tetap ringan, beberapa berkas *generated*/sementara tidak disertakan (lihat `.gitignore`):

- `node_modules/` — dependensi tool, bisa dipasang ulang (mis. `npm install`).
- `undefined/` — cache tool.
- Berkas *lock* sementara MS Office (`~$*.docx`).

Seluruh materi skripsi (draf, analisis literatur, dan PDF referensi) **sudah** disertakan di repositori ini.
