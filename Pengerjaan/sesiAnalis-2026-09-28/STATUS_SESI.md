# Status Akhir Sesi

## Status filesystem saat arsip dibuat

- `Pengerjaan/` memang kosong sejak awal sebelum sesi ini; tidak ada project lama yang hilang.
- Artefak yang dibuat selama sesi ternyata tidak persist pada filesystem, sehingga arsip ini menjadi catatan resmi untuk melanjutkan.
- `Pengerjaan/sesiAnalis-2026-09-28/`: dibuat tanpa memindahkan, menghapus, atau menimpa file lain.
- `.venv` dan notebook hasil kerja sebelumnya tidak terlihat pada workspace saat arsip dibuat.
- File sumber di `code/` tetap tersedia.

## Riwayat pekerjaan sesi sebelumnya

SEBELUM workspace ter-reset, sesi sebelumnya sudah:

- Membaca dokumen penjelasan judul, arsip Bab 1, catatan dosen, dan analisis literatur.
- Menyusun PRD dan struktur folder project.
- Membuat implementasi Python package `hijaiyah_ocr` dengan modul data, manifest, preprocessing, model, metrics, checkpoint, training, demo, dan CLI.
- Membuat konfigurasi demo dan production.
- Membuat data demo sintetis dengan tiga penulis dan split participant-wise.
- Melakukan smoke test CLI untuk stage 1 backbone dan stage 2 CNN-LSTM.
- Membuat dan memvalidasi `notebooks/training_hijaiyah_colab.ipynb` dengan 16 sel.
- Merevisi README dan dokumentasi agar notebook menjadi entrypoint utama.
- Menambah dependensi Jupyter untuk eksekusi notebook lokal.
- Menambah test penolakan harakat, huruf Latin, dan hamza terpisah.

## Hasil yang pernah tercatat

- Python virtual environment: 3.12.
- PyTorch: 2.14 CPU.
- timm: 1.0.30.
- Test sebelum penambahan test notebook: 7 lulus.
- Ruff: lulus.
- Mypy: lulus untuk 12 file source.
- Smoke test: 12 sampel, 3 penulis, train/validation/test masing-masing 4.
- Bobot ImageNet MobileNetV4 berhasil diuji.
- Metrik smoke adalah sintetis dan tidak boleh digunakan sebagai hasil penelitian.

## Pemeriksaan terakhir yang gagal

Setelah dependensi Jupyter dipasang, pemeriksaan ulang tidak dapat berjalan karena `.venv`, source project, dan notebook tidak lagi ada pada filesystem yang aktif. Karena itu status code dan test terbaru tidak diklaim lulus.

## Yang belum selesai

- Rekonstruksi folder project bila masih diperlukan.
- Menjalankan notebook `.ipynb` sampai selesai.
- Menjalankan test baru penolakan harakat/hamza.
- Menyimpan checkpoint dan hasil evaluasi final di folder artifacts.
- Mengganti data demo dengan data Iqro 3 nyata.
