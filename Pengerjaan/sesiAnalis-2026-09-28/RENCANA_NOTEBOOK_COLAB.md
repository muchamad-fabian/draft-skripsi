# Rencana Notebook Google Colab

Nama file yang direkomendasikan: `notebooks/training_hijaiyah_colab.ipynb`

## Sel yang diperlukan

1. Judul dan kontrak output.
2. Instalasi dependency dengan `%pip install`.
3. Deteksi `PROJECT_ROOT` dan penambahan `src` ke `sys.path`.
4. Import modul package.
5. Pengaturan `USE_DEMO_DATA`, `USE_PRETRAINED`, `EPOCHS`, `BATCH_SIZE`, `NUM_WORKERS`, dan `SAVE_TO_GOOGLE_DRIVE`.
6. Deteksi Colab dan mount Google Drive bila tersedia.
7. Pembuatan data demo atau pembacaan manifest nyata.
8. Validasi manifest dan whitelist.
9. Stage 1: `train_backbone`.
10. Stage 2: `train_crnn` dengan checkpoint stage 1.
11. Evaluasi split test.
12. Prediksi satu citra.
13. Assertion bahwa prediksi hanya berisi 28 huruf.
14. Penyalinan checkpoint dan JSON ke Google Drive.

## Perilaku data demo

- Tiga writer: train, validation, test.
- Minimal dua sampel per writer.
- Label 2–3 huruf.
- Sebagian citra memakai garis titik-titik.
- Metrik hanya validasi software.

## Perilaku data nyata

- Manifest dibaca dari `REAL_MANIFEST_PATH`.
- `USE_DEMO_DATA = False`.
- Checkpoint tidak boleh ditimpa diam-diam; gunakan folder eksperimen bertanggal.
- Data writer tidak boleh bocor antar split.

## Bukti keberhasilan notebook

- Tidak ada error pada semua sel.
- `backbone_best.pt` dan `crnn_best.pt` terbentuk.
- `evaluation.json` dan `prediction.json` terbentuk.
- Assertion output lolos.
- Ringkasan metrik dicatat di jurnal sesi.

## Catatan Colab

- Gunakan GPU bila tersedia.
- Bobot ImageNet memerlukan koneksi internet.
- Simpan artifact ke Drive sebelum runtime berakhir.
- Jika hanya mengunggah notebook, source `src/hijaiyah_ocr` juga harus diunggah atau dipasang.
